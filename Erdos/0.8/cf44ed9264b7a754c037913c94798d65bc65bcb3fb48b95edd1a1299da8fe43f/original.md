```
incidence_matrix(g::AGraphOrDiGraph, T::DataType=Int; oriented=false)
```

Returns a sparse node-arc incidence matrix for a graph, indexed by `[v, i]`, where `i` is in `1:ne(g)`, indexing an edge `e`. For directed graphs, a value of `-1` indicates that `src(e) == v`, while a value of `1` indicates that `dst(e) == v`. Otherwise, the value is `0`.

For undirected graphs, both entries are `1` if `oriented=false`, otherwise `[v, i] -> -1` and `[u, i] -> 1` if `v < u`.
