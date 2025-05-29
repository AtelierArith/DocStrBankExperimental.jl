```
struct OpaqueContent
```

Represents opaque content with a specific MIME type.

Constructors:

```julia
OpaqueContent(data::AbstractVector{UInt8}, mime::MIME)

OpaqueContent(mime::MIME) do io
    # add something to io::IO
end
```

Example:

content = OpaqueContent(MIME("text/html")) do io     println(io, "<p>Hello, World!</p>") end lazyreport(content)
