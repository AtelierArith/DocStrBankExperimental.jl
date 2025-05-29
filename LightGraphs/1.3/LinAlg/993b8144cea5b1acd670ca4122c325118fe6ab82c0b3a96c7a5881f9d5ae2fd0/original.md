```
adjacency_matrix(g[, T=Int; dir=:out])
```

Return a sparse adjacency matrix for a graph, indexed by `[u, v]` vertices. Non-zero values indicate an edge from `u` to `v`. Users may override the default data type (`Int`) and specify an optional direction.

### Optional Arguments

`dir=:out`: `:in`, `:out`, or `:both` are currently supported.

### Implementation Notes

This function is optimized for speed and directly manipulates CSC sparse matrix fields.
