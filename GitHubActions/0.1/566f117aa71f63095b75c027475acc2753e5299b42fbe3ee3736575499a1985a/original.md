```
GitHubActionsLogger(level)
```

A logger that prints to standard output in the format expected by GitHub Actions.

By default, GitHubActionsLogger inspects the [`RUNNER_DEBUG` environment variable](https://docs.github.com/en/actions/learn-github-actions/variables) to match the log-level to that set in GitHub Actions.
