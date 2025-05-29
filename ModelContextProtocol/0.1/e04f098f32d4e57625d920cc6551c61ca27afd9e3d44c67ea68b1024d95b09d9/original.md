```
ImageContent(; data::Vector{UInt8}, mime_type::String, annotations::Dict{String,Any}=Dict{String,Any}()) <: Content
```

Image-based content for MCP protocol messages.

# Fields

  * `type::String`: Content type identifier (always "image")
  * `data::Vector{UInt8}`: The binary image data
  * `mime_type::String`: MIME type of the image (e.g., "image/png")
  * `annotations::Dict{String,Any}`: Optional metadata about the content
