```
query(db::Surreal; sql::String, vars::Union{Dict, Nothing}=nothing)
```

Runs a set of SurrealQL statements against the database.

# Arguments

`sql`: Specifies the SurrealQL statements. `vars`: Assigns variables which can be used in the query.

# Returns

The records.

# Examples

```jldoctest
julia> # Assign the variable on the connection
julia> result = query(db, sql=r"create person; select * from type::table($tb)",vars=Dict("tb"=> "person"))
julia> # Get the first result from the first query
julia> result[0]["result"][0]
julia> # Get all of the results from the second query
julia> result[1]["result"]
```
