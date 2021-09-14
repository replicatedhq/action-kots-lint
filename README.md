action-kots-lint
=====================

A github Action to lint application manifests for a [Replicated KOTS](https://blog.replicated.com/announcing-kots/) application.

### Usage

An example workflow is included at [./.github/workflows/main.yml](./.github/workflows/main.yml)

```yaml
name: Lint KOTS Application Manifests

on: [push]

jobs:
  create-release:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v1
    - uses: replicatedhq/action-kots-lint@v0.2.0
      name: Lint the release manifests
      with:
        replicated-api-token: ${{ secrets.REPLICATED_API_TOKEN }}
        replicated-app: ${{ secrets.REPLICATED_APP }}
        yaml-dir: manifests
```

### Inputs

#### replicated-app

The application slug or ID for this application. This can be found at [vendor.replicated.com/settings](https://vendor.replicated.com/settings).

#### replicated-api-token

A Replicated Service Account API token (create one at vendor portal under [Service Accounts](https://vendor.replicated.com/team/serviceaccounts)).

#### yaml-dir

A directory containing KOTS manifests, defaults to `./manifests`.


### Limiting to specific branches or patterns

To limit which branches create releases or more advanced branch filtering, check out the [GitHub Actions docs on workflow triggers](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows).
