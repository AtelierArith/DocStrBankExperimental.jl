```julia
mime_from_extension(query::AbstractString[, default::T=nothing])::Union{MIME,T}
```

# Examples:

```julia
mime_from_extension(".json") == MIME"application/json"()
mime_from_extension("html") == MIME"text/html"()
mime_from_extension("asdfff") == nothing
mime_from_extension("asdfff", MIME"text/plain"()) == MIME"text/plain"()
```
