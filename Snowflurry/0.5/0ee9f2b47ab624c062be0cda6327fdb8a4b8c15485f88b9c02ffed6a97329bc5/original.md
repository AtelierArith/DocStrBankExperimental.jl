```
get_status_type(s::Status)::String
```

Returns the type associated with the `Status` of a quantum computation.

See [`Status`](@ref) for more details about possible `type` strings.

# Examples

```jldoctest
julia> get_status_type(Status(type = "SUCCEEDED"))
"SUCCEEDED"

```
