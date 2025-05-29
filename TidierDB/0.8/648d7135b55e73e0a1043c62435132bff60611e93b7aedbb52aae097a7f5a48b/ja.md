```
show_tables(con; GBQ_datasetname)
```

データベースで利用可能なテーブルを表示します。現在、DuckDB、databricks、Snowflake、GBQ、SQLite、LibPQをサポートしています。

# 引数

  * `con` : バックエンドへの接続
  * `GBQ_datasetname` : データセット名の文字列

# 例

```jldoctest
julia> db = connect(duckdb());

julia> show_tables(db);
```
