```
 write_file(sql_query::SQLQuery, path)
```

sql_queryからローカルファイルを書き込みます。現時点ではDuckDBのみをサポートしています。

# 引数

  * `sql_query`: SQLクエリ
  * `path`: ファイルタイプのサフィックスを持つファイルパス、例: "path.csv", "path.parquet" など

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(a = ["1-1", "2-2", "3-3-3"]); 

julia> @chain dt(db, df, "df") @filter(a == "2-2") write_file("test.parquet")
(Count = [1],)
```
