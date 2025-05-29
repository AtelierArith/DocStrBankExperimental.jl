```
DBInterface.execute(db::SQLite.DB, sql::String, [params])
DBInterface.execute(stmt::SQLite.Stmt, [params])
```

Bind any positional (`params` as `Vector` or `Tuple`) or named (`params` as `NamedTuple` or `Dict`) parameters to an SQL statement, given by `db` and `sql` or as an already prepared statement `stmt`, execute the query and return an iterator of result rows.

Note that the returned result row iterator only supports a single-pass, forward-only iteration of the result rows. Calling `SQLite.reset!(result)` will re-execute the query and reset the iterator back to the beginning.

The resultset iterator supports the [Tables.jl](https://github.com/JuliaData/Tables.jl) interface, so results can be collected in any Tables.jl-compatible sink, like `DataFrame(results)`, `CSV.write("results.csv", results)`, etc.

Passing `strict=true` to `DBInterface.execute` will cause the resultset iterator to return values of the exact type specified by SQLite.
