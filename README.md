# Pull Request Branch Name Checker
[![CI](https://github.com/pcarney8/pr-branch-name-checker/workflows/CI/badge.svg)](https://github.com/pcarney8/pr-branch-name-checker/actions?query=workflow%3ACI)
[![GitHub Marketplace]()](https://github.com/marketplace/actions/pr-branch-name-checker)

A GitHub Action that checks your Pull Request code for the name of the Pull Request branch to prevent you from committing the current branch name to the target branch

## How does it work?

Create a GitHub action on all Pull Requests that are not draft and add this action to your `.github/workflows/` directory:
```yaml
name: Check PR code for branch name

on:
  pull_request:

jobs:
  check_pr_for_branch_name:
    if: github.event.pull_request.draft == false
    name: check pr for branch name
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Check PR for branch name
        uses: pcarney8/pr-branch-name-checker@v1
```

