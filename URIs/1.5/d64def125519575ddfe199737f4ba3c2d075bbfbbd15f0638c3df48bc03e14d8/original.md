```
queryparampairs(::URI) -> Vector{Pair{String, String}}
queryparampairs(query_str::AbstractString) -> Vector{Pair{String, String}}
```

Identical to `queryparams`, but returns a `Vector{Pair{String, String}}` containing the `query` parameter string parsed according to the key=value pair formatting convention.

Note that this is not part of the formal URI grammar, merely a common parsing convention — see [RFC 3986](https://tools.ietf.org/html/rfc3986#section-3.4).
