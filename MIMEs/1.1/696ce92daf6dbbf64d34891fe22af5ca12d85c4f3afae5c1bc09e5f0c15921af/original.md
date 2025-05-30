```julia
extension_from_mime(mime::MIME[, default::T=""])::Union{String,T}
```

Return the most common file extension used for files of the given MIME type.

# Examples:

```julia
extension_from_mime(MIME"application/json"()) == ".json"
extension_from_mime(MIME"text/html"()) == ".html"
extension_from_mime(MIME"text/blablablaa"()) == ""
extension_from_mime(MIME"text/blablablaa"(), ".bin") == ".bin"
```
