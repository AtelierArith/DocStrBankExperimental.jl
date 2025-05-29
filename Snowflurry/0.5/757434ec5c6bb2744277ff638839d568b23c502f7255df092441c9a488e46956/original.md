```
get_status_message(s::Status)::String
```

Returns the message associated with the `Status` of a quantum computation.

# Examples

```jldoctest
julia> get_status_message(Status(type = "FAILED", message = "something failed"))
"something failed"

```
