```
MCPResource(; uri, name, description="", mime_type="application/json", 
          data_provider, annotations=Dict{String,Any}()) -> MCPResource
```

Create a resource with automatic URI conversion from strings.

# Arguments

  * `uri`: String or URI identifier for the resource
  * `name`: Human-readable name for the resource
  * `description`: Detailed description
  * `mime_type`: MIME type of the resource
  * `data_provider`: Function that returns the resource data when called
  * `annotations`: Additional metadata for the resource

# Returns

  * `MCPResource`: A new resource with the provided configuration
