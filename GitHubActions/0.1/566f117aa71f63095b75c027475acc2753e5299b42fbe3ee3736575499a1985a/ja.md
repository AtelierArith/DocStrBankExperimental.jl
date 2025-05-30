```
GitHubActionsLogger(level)
```

GitHub Actionsが期待する形式で標準出力に出力するロガーです。

デフォルトでは、GitHubActionsLoggerは[`RUNNER_DEBUG`環境変数](https://docs.github.com/en/actions/learn-github-actions/variables)を調査して、ログレベルをGitHub Actionsで設定されたものに一致させます。
