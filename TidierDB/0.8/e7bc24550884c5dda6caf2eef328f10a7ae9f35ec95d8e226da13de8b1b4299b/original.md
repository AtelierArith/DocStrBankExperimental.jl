```
drop_view(sql_query, name)
```

Drop a view. Currently supports DuckDB, MySQL, GBQ, Postgres

# Arguments

  * `sql_query`: The SQL query to create a view from.
  * `name`: The name of the view to drop.

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> @chain dt(db, df, "df1") @create_view(viewer);

julia> drop_view(db, "viewer");
```
