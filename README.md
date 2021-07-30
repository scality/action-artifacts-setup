# action-setup-artifacts

The goal of this action is to set GitHub Actions outputs to interact with [Artifacts].

## Outputs

This action will output the following variables:

* `artifacts-name`: Will contain a generated name for the artifacts that will be used for a workflow. Each workflow will have a unique artifact name which can be shared among the jobs that are within.
* `artifacts-link`: Will contain the full url where the artifacts can be downloaded.

## Examples

### Simple usage of the action

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: scality/action-artifacts-setup@v1
```

### Downloading a previously uploaded file

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - id: artifacts
        uses: scality/action-artifacts-setup@v1
      - run: |
          curl ${{ steps.artifacts.outputs.artifact-link }}/my-file -o my-file
```


[Artifacts]: https://github.com/scality/artifacts
