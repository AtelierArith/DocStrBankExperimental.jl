```
resolvereference(base::Union{URI,AbstractString}, ref::Union{URI,AbstractString}) -> URI
```

Resolve a URI reference `ref` relative to the absolute base URI `base`, complying with [RFC 3986 Section 5.2](https://tools.ietf.org/html/rfc3986#section-5.2).

If `ref` is an absolute URI, return `ref` unchanged.

# Examples

```jldoctest; setup = :(using URIs)
julia> u = resolvereference("http://example.org/foo/bar/", "/baz/")
URI("http://example.org/baz/")

julia> resolvereference(u, "./hello/world")
URI("http://example.org/baz/hello/world")

julia> resolvereference(u, "http://localhost:8000")
URI("http://localhost:8000")
```
