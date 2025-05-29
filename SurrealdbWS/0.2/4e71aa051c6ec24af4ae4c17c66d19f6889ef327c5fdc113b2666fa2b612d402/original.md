```
signin(db::Surreal; user::String, pass::String)::Union{String, Nothing}
```

Signs this connection in to a specific authentication scope.

# Arguments

  * `user`: username in signin query
  * `pass`: password in signin query

# Examples:

```jldoctest
julia> signin(db, user="root", pass="root")
```
