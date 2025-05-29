```
adjacency_matrix(g, dir=:out, T::DataType=Int)
```

Returns a sparse boolean adjacency matrix for a graph, indexed by `[u, v]` vertices. `true` values indicate an edge between `u` and `v`. Users may specify a direction (`:in`, `:out`, or `:all` are currently supported; `:out` is default for both directed and undirected graphs) and a data type for the matrix (defaults to `Int`).
