```
CallToolResult(; content::Vector{Dict{String,Any}}, is_error::Bool=false) <: ResponseResult
```

Result returned from a tool invocation.

# Fields

  * `content::Vector{Dict{String,Any}}`: Content produced by the tool
  * `is_error::Bool`: Whether the tool execution resulted in an error
