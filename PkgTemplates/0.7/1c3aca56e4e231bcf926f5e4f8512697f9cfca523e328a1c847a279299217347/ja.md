```
CodeOwners <: Plugin
CodeOwners(; owners)
```

GitLab/GitHub 互換の CODEOWNERS ファイルを作成するプラグインです。owners は、オーナー名のベクトルにマッピングされたパターンのベクトルである必要があります。例えば: `owners=["*"=>["@invenia"], "README.md"=>["@documentation","@oxinabox]]` は、すべてのファイルに対する一般的な所有権を invenia グループに割り当てますが、readme の所有権は documentation グループとユーザー oxinabox に割り当てます。

デフォルトでは、空の CODEOWNERS ファイルを作成します。
