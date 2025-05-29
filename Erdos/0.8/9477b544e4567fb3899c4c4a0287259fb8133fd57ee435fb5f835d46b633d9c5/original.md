```
edges(g, v)
```

Returns an iterator to the edges in `g` coming from vertex `v`. `v == src(e)` for each returned edge `e`.

It is equivalent to [`out_edges`](@ref).

For digraphs, use [`all_edges`](@ref) to iterate over both in and out edges.
