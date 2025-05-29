```
EmbeddedResource(; resource::Union{TextResourceContents, BlobResourceContents}, 
                annotations::Dict{String,Any}=Dict{String,Any}()) <: Content
```

Embedded resource content as defined in MCP schema.

# Fields

  * `type::String`: Content type identifier (always "resource")
  * `resource::Union{TextResourceContents, BlobResourceContents}`: The embedded resource content
  * `annotations::Dict{String,Any}`: Optional metadata about the resource
