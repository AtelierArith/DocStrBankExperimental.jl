```
MCPResource(; uri, name::String, description::String="",
          mime_type::String="application/json", data_provider::Function,
          annotations::Dict{String,Any}=Dict{String,Any}()) <: Resource
```

Implement a resource that clients can access in the MCP protocol. Resources represent data that can be read by models and tools.

# Fields

  * `uri::URI`: Unique identifier for the resource
  * `name::String`: Human-readable name for the resource
  * `description::String`: Detailed description of the resource
  * `mime_type::String`: MIME type of the resource data
  * `data_provider::Function`: Function that provides the resource data when called
  * `annotations::Dict{String,Any}`: Additional metadata for the resource
