```
queryparams(::URI) -> Dict
queryparams(query_str::AbstractString) -> Dict
```

Returns a `Dict` containing the `query` parameter string parsed according to the key=value pair formatting convention.

Note that duplicate query param values are not supported; if needed, use `queryparampairs`.

Note that this is not part of the formal URI grammar, merely a common parsing convention — see [RFC 3986](https://tools.ietf.org/html/rfc3986#section-3.4).
