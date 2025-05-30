```julia
contenttype_from_mime(mime::MIME)::String
```

Turn a MIME into a Content-Type header value, which might include the `charset` parameter.

# Examples:

```julia
contenttype_from_mime(MIME"application/json"()) == "application/json; charset=utf-8"
contenttype_from_mime(MIME"application/x-bogus"()) == "application/x-bogus"
contenttype_from_mime(mime_from_extension(".png", MIME"application/octet-stream"())) == "image/png"
```

# See also:

[`charset_from_mime`](@ref), [`mime_from_contenttype`](@ref)
