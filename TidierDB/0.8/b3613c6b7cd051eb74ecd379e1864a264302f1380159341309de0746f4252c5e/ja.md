```
   copy_to(conn, df_or_path, "name"; overwrite = false )
```

ユーザーがデータフレームをデータベース接続にコピーできるようにします。現在、DuckDB、SQLite、MySqlをサポートしています。

# 引数

  * `conn`: データベース接続
  * `df`: コピーされるデータフレームまたはソースとして使用されるパス。DuckDBでは、パスは.csv、.json、.parquetをサポートします。
  * `name`: 使用されるデータベースの名前を文字列として指定
  * `overwrite`: 選択した名前のテーブルが存在する場合に上書きされるかどうか、デフォルトは`false`

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> copy_to(db, df, "test");
```
