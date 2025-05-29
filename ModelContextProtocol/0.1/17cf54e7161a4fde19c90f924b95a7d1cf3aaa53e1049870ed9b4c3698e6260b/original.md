```
TextContent(; text::String, annotations::Dict{String,Any}=Dict{String,Any}()) <: Content
```

Text-based content for MCP protocol messages.

# Fields

  * `type::String`: Content type identifier (always "text")
  * `text::String`: The actual text content
  * `annotations::Dict{String,Any}`: Optional metadata about the content
