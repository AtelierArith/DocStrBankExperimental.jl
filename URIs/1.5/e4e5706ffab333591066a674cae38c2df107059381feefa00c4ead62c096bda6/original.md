```
absuri(uri::Union{URI,AbstractString}, context::Union{URI,AbstractString}) -> URI
```

Construct an absolute URI, using `uri.path` and `uri.query` and filling in other components from `context`.
