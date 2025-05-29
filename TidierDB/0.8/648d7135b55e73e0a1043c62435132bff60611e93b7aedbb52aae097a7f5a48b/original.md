```
show_tables(con; GBQ_datasetname)
```

Shows tables available in database. currently supports DuckDB, databricks, Snowflake, GBQ, SQLite, LibPQ

# Arguments

  * `con` : connection to backend
  * `GBQ_datasetname` : string of dataset name

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> show_tables(db);
```
