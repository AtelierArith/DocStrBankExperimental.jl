```
BlobResourceContents(; uri::String, blob::Vector{UInt8}, mime_type::Union{String,Nothing}=nothing) <: ResourceContents
```

Binary contents for MCP resources.

# Fields

  * `uri::String`: Unique identifier for the resource
  * `blob::Vector{UInt8}`: The binary content of the resource
  * `mime_type::Union{String,Nothing}`: Optional MIME type of the content
