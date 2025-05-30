```julia
charset_from_mime(mime::MIME[, default::T=nothing])::Union{String,T}
```

The default charset associated with this type, if any. If not known, text MIMEs default to "UTF-8". Possible values are: Union{Nothing, String}["UTF-8", "US-ASCII", "7-BIT", nothing].

# Examples:

```julia
charset_from_mime(MIME"application/json"()) == "UTF-8"
charset_from_mime(MIME"application/x-bogus"()) == nothing
charset_from_mime(MIME"text/blablablaa"()) == "UTF-8" # because it is a `text/` mime
charset_from_mime(MIME"text/blablablaa"(), "LATIN-1") == "LATIN-1"
```
