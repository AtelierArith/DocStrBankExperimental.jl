```julia
mime_from_path(path::AbstractString[, default::T=nothing])::Union{MIME,T}
```

Return the MIME type of the file at `path`, based on the file extension.

# Examples:

```julia
mime_from_path("hello.json") == MIME"application/json"()
mime_from_path("/home/fons/wow.html") == MIME"text/html"()
mime_from_path("/home/fons/wow") == nothing
mime_from_path("/home/fons/wow", MIME"text/plain"()) == MIME"text/plain"()
```
