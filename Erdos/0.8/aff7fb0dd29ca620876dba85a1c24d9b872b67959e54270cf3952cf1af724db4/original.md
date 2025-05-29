```
neighbors(g, v)
```

Returns a list of all neighbors from vertex `v` in `g`.

For directed graph, this is equivalent to [`out_neighbors`](@ref)(g, v).

NOTE: it may return a reference, not a copy. Do not modify result.
