```
resolvereference(base::Union{URI,AbstractString}, ref::Union{URI,AbstractString}) -> URI
```

URI参照`ref`を絶対ベースURI`base`に対して解決し、[RFC 3986 セクション 5.2](https://tools.ietf.org/html/rfc3986#section-5.2)に準拠します。

`ref`が絶対URIである場合、`ref`をそのまま返します。

# 例

```jldoctest; setup = :(using URIs)
julia> u = resolvereference("http://example.org/foo/bar/", "/baz/")
URI("http://example.org/baz/")

julia> resolvereference(u, "./hello/world")
URI("http://example.org/baz/hello/world")

julia> resolvereference(u, "http://localhost:8000")
URI("http://localhost:8000")
```
