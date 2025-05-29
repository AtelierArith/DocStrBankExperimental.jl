```
filter_vertices(g, prop[, val])
filter_vertices(g, fn)
```

Return an iterator to all vertices that have property `prop` defined (optionally as `val`), or where function `fn` returns `true` only for vertices that should be included in the iterator.

`fn` should be of the form

```
fn(g::AbstractMetaGraph, v::Integer)::Boolean
```

where `v` is replaced with the vertex being evaluated.
