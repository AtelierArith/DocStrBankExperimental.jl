```
filter_edges(g, prop[, val])
filter_edges(g, fn)
```

Return an iterator to all edges that have property `prop` defined (optionally as `val`), or where function `fn` returns `true` only for edges that should be included in the iterator.

`fn` should be of the form

```
fn(g::AbstractMetaGraph{T}, e::SimpleEdge{T})::Boolean
```

where `e` is replaced with the edge being evaluated.
