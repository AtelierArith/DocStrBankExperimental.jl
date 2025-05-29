```
CallToolParams(; name::String, arguments::Union{Dict{String,Any},Nothing}=nothing) <: RequestParams
```

Parameters for invoking a specific tool on an MCP server.

# Fields

  * `name::String`: Name of the tool to call
  * `arguments::Union{Dict{String,Any},Nothing}`: Optional arguments to pass to the tool
