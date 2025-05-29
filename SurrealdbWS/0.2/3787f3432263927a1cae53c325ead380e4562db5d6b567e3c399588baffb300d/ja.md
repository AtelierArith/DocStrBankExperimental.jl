```
delete(db::Surreal; thing::String)
```

データベースからテーブル内のすべてのレコード、または特定のレコードを削除します。この関数はデータベース内で次のクエリを実行します: delete * from `thing`

# 引数

`thing`: 削除するテーブル名またはレコードID。

# 例

julia> # テーブルからすべてのレコードを削除 julia> delete(db, "person") julia> # テーブルから特定のレコードを削除 julia> delete(db, "person:h5wxrf2ewk8xjxosxtyc")
