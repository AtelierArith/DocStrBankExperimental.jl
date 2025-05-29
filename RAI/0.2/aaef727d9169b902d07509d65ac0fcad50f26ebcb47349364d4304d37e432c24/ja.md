```
create_database(ctx, name::String[, source::String])
```

指定された `name` でデータベースを作成し、オプションで既存の `source` からクローンします。注意: 既に存在するデータベースを作成することはエラー (`HTTPError(400)`) です。データベースを上書きするには、まず `delete_database(ctx, name)` を実行し、その後に作成する必要があります。
