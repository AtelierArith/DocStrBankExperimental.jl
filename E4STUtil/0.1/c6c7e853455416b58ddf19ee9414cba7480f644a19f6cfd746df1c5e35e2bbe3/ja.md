```
register_e4st_dep(name, message, remote_path, args...; kwargs...)
```

`DataDeps.DataDep`のドキュメントを参照してください。必要なフィールドは次のとおりです。

  * name - メタデータの名前。後で`datadep"<name>"`または[`get_e4st_dep`](@ref)を使用してアクセスします。
  * message - メタデータに保存するメッセージ。データの出所、サイズなどの説明。
  * remote_path - データを取得する場所。
