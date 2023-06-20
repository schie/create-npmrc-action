# Create .npmrc Action

This action creates an `.npmrc` file at the root of your repository to authenticate with private npm registries.

## Inputs

### `registries`

**Required** A multi-line string containing your registry URLs and their corresponding auth tokens. Each registry should be defined on two lines: the first line is the registry URL, and the second line is the authentication token for that registry.

## Example usage

This action can be used as follows within a workflow:

```yaml
steps:
  - name: Checkout
    uses: actions/checkout@v2

  - name: Create .npmrc
    uses: schie/create-npmrc-action@main
    with:
      registries: |
        registry=https://your-private-registry1/
        //your-private-registry1/:_authToken=${{ secrets.NPM_AUTH_TOKEN1 }}
        registry=https://your-private-registry2/
        //your-private-registry2/:_authToken=${{ secrets.NPM_AUTH_TOKEN2 }}

  - name: SAM Build
    run: sam build
```

In this example, `https://your-private-registry1/` and `https://your-private-registry2/` with your actual private NPM registry URLs. The secrets `NPM_AUTH_TOKEN1` and `NPM_AUTH_TOKEN2` should be set in your repository's settings.

## License

This project is licensed under the terms of the MIT license.
