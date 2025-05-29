```
ErrorInfo(; code::Int, message::String, data::Union{Dict{String,Any},Nothing}=nothing)
```

Error information structure for JSON-RPC error responses.

# Fields

  * `code::Int`: Numeric error code (predefined in ErrorCodes module)
  * `message::String`: Human-readable error description
  * `data::Union{Dict{String,Any},Nothing}`: Optional additional error details
