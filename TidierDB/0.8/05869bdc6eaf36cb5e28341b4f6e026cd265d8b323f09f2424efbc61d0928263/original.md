```
@create_view(sql_query, name, replace = true)
```

Create a view from a SQL query. Currently supports DuckDB, MySQL, GBQ, Postgres

# Arguments

  * `sql_query`: The SQL query to create a view from.
  * `name`: The name of the view to create.
  * `replace`: Boolean value that defaults to false so as not to replace exisiting views

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> @chain dt(db, df, "df1") @create_view(viewer); # will not overwrite existing view

julia> dt(db, "viewer");

julia> @chain dt(db, df, "df1") @create_view(viewer, true); # will overwrite exisiting view
```
