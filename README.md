# Github reusable actions

## branch-name

Gives the branch-name for the current workflow. The following `event_name` are currently supported ([see github actions events](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#available-events))
- `push`
- `pull_Request`
- `workflow_dispatch`

### How to use

```
name: Get Branch Name and Action Type
on:
  workflow_dispatch:
    push:
    pull_request:
    types: [synchronize, labeled]

jobs:
  get_info:
    runs-on: ubuntu-latest
    steps:
      - name: Get Branch Name
        id: branch-name
        uses: stephdotnet/branch-name/branch-name@main
      - name: Print branch name and action type
        env:
          BRANCH_NAME: ${{ steps.branch-name.outputs.branch-name }}
        run: echo "Branch Name: $BRANCH_NAME"
```
