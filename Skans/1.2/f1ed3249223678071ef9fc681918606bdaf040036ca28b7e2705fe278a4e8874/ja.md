```
GitHubRepo(;
    dir=mktempdir(),
    user=ENV["GITHUB_ACTOR"],
    token=ENV["GITHUB_TOKEN"],
    repo=ENV["GITHUB_REPOSITORY"],
    branch="skan"
)
```

GitHub Runner上で実行する場合、追加の情報は必要ありません。トークンとリポジトリは`GITHUB_TOKEN`と`GITHUB_REPOSITORY`を介して取得できます。公開リポジトリの場合、`token`を空の文字列`""`に設定します。`repo`は`octocat/Hello-World`の形式です。
