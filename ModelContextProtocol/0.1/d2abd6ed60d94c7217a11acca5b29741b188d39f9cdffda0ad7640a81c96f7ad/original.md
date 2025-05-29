```
TextResourceContents(; uri::String, text::String, mime_type::Union{String,Nothing}=nothing) <: ResourceContents
```

Text-based contents for MCP resources.

# Fields

  * `uri::String`: Unique identifier for the resource
  * `text::String`: The text content of the resource
  * `mime_type::Union{String,Nothing}`: Optional MIME type of the content
