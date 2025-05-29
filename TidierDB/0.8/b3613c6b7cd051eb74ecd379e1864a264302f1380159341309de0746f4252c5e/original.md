```
   copy_to(conn, df_or_path, "name"; overwrite = false )
```

Allows user to copy a df to the database connection. Currently supports DuckDB, SQLite, MySql

# Arguments

  * `conn`: the database connection
  * `df`: dataframe to be copied or path to serve as source. With DuckDB, path supports .csv, .json, .parquet
  * `name`: name as string for the database to be used
  * `overwrite`: whether or not table with chosen name should be overwritten if it exists, defaults to `false`

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> copy_to(db, df, "test");
```
