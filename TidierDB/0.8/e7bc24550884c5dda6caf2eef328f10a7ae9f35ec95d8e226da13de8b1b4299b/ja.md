```
drop_view(sql_query, name)
```

ビューを削除します。現在、DuckDB、MySQL、GBQ、Postgresをサポートしています。

# 引数

  * `sql_query`: ビューを作成するためのSQLクエリ。
  * `name`: 削除するビューの名前。

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> @chain dt(db, df, "df1") @create_view(viewer);

julia> drop_view(db, "viewer");
```
