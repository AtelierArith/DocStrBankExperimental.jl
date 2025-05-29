```
query(db::ENDB, sql::String, params; bulk::Bool=false)
```

Send a query to the database and return the resultset.

```julia-repl
julia> endb = ENDB()
ENDB("http://localhost:3803/sql", Dict{Any, Any}())

julia> query(endb, "SELECT 1")
1-element JSON3.Array{JSON3.Array, Vector{UInt8}, Vector{UInt64}}:
 [1]
```
