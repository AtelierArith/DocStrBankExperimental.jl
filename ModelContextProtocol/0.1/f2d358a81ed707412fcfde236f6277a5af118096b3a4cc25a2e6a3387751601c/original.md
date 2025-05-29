```
ToolParameter(; name::String, description::String, type::String, required::Bool=false)
```

Define a parameter for an MCP tool.

# Fields

  * `name::String`: The parameter name (used as the key in the params dictionary)
  * `description::String`: Human-readable description of the parameter
  * `type::String`: Type of the parameter as specified in the MCP schema (e.g., "string", "number", "boolean")
  * `required::Bool`: Whether the parameter is required for tool invocation
