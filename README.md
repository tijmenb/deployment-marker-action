[![Community Project header](https://github.com/newrelic/open-source-office/raw/master/examples/categories/images/Community_Project.png)](https://github.com/newrelic/open-source-office/blob/master/examples/categories/index.md#category-community-project)

# New Relic Application Deployment Marker

[![GitHub Marketplace version](https://img.shields.io/github/release/newrelic/deployment-marker-action.svg?label=Marketplace&logo=github)](https://github.com/marketplace/actions/new-relic-application-deployment-marker)

A GitHub Action to add New Relic deployment markers during your release pipeline.

## Inputs

| Key             |          | Description                                                                                                                              |
| --------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `apiKey`        | required | Your New Relic [personal API key](https://docs.newrelic.com/docs/apis/get-started/intro-apis/types-new-relic-api-keys#personal-api-key). |
| `applicationId` | required | The New Relic application ID to apply the deployment marker.                                                                             |
| `revision`      | required | Metadata to apply to the deployment marker - e.g. the latest release tag                                                                 |
| `user`          | optional | The user creating the deployment. Default: `github.actor`                                                                                |
| `region`        | optional | The region of your New Relic account. Default: `US`                                                                                      |
| `accountId`     | optional | The account number the application falls under. This could also be a subaccount.                                                         |

## Example usage

```yaml
# Add a New Relic application deployment marker on release
on:
  - release

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Apply New Relic deployment marker
        uses: newrelic/deployment-marker-action@master
        with:
          apiKey: ${{ secrets.NEW_RELIC_API_KEY }}
          applicationId: <your application ID>
          revision: "${{ github.ref }}-${{ github.sha }}"
          user: "${{ github.actor }}"                     # optional
          region: US                                      # optional
          accountId: <your New Relic account ID>          # optional
```