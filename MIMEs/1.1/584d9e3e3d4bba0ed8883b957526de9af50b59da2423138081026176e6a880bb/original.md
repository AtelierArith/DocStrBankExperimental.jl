```julia
mime_from_contenttype(content_type::String[, default::T=nothing])::Union{MIME,T}
```

Extract a MIME from a Content-Type header value. If the input is empty, `default` is returned.

# Examples:

```julia
mime_from_contenttype("application/json; charset=utf-8") == MIME"application/json"()
mime_from_contenttype("application/x-bogus") == MIME"application/x-bogus"()
mime_from_contenttype("") == nothing
mime_from_contenttype("", MIME"application/octet-stream"()) == MIME"application/octet-stream"()
```

# See also:

[`contenttype_from_mime`](@ref)
