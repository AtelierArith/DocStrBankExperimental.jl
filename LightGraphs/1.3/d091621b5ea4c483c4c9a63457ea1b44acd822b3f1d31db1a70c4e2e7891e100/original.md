```
simplecycles_limited_length(g, n, ceiling=10^6)
```

Compute and return at most `ceiling` cycles of length at most `n` of the given graph. Both directed and undirected graphs are supported.

### Performance

The number of cycles grows very fast with the number of vertices and the allowed length of the cycles. This function is intended for finding short cycles. If you want to find cycles of any length in a directed graph, [`simplecycles`](@ref) or [`simplecycles_iter`](@ref) may be more efficient.
