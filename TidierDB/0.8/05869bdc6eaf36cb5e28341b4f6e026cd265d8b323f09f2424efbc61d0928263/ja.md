```
@create_view(sql_query, name, replace = true)
```

SQLクエリからビューを作成します。現在、DuckDB、MySQL、GBQ、Postgresをサポートしています。

# 引数

  * `sql_query`: ビューを作成するためのSQLクエリ。
  * `name`: 作成するビューの名前。
  * `replace`: 既存のビューを置き換えないようにデフォルトでfalseのブール値。

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> @chain dt(db, df, "df1") @create_view(viewer); # 既存のビューを上書きしません

julia> dt(db, "viewer");

julia> @chain dt(db, df, "df1") @create_view(viewer, true); # 既存のビューを上書きします
```
