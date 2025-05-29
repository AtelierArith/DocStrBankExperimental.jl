```
authenticate(db::Surreal; token::Union{String, Nothing}=nothing)::Nothing
```

Authenticates the current connection with a JWT token.

# Arguments

  * `token`: The token to use for the connection.

# Examples

```jldoctest
julia> authenticate(db, token="JWT token here")
```
