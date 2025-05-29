```
 write_file(sql_query::SQLQuery, path)
```

Write a local file to from sql_query. Only supports DuckDB at this time.

# Arguments

  * `sql_query`: The SQL query
  * `path`: file path with file type suffix ie "path.csv", "path.parquet", etc

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(a = ["1-1", "2-2", "3-3-3"]); 

julia> @chain dt(db, df, "df") @filter(a == "2-2") write_file("test.parquet")
(Count = [1],)
```
