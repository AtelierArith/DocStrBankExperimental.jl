```
GetPromptParams(; name::String, arguments::Union{Dict{String,String},Nothing}=nothing) <: RequestParams
```

Parameters for requesting a specific prompt from an MCP server.

# Fields

  * `name::String`: Name of the prompt to retrieve
  * `arguments::Union{Dict{String,String},Nothing}`: Optional arguments to apply to the prompt template
