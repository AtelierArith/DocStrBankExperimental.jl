```
incidence_matrix(g[, T=Int; oriented=false])
```

Return a sparse node-arc incidence matrix for a graph, indexed by `[v, i]`, where `i` is in `1:ne(g)`, indexing an edge `e`. For directed graphs, a value of `-1` indicates that `src(e) == v`, while a value of `1` indicates that `dst(e) == v`. Otherwise, the value is `0`. For undirected graphs, both entries are `1` by default (this behavior can be overridden by the `oriented` optional argument).

If `oriented` (default false) is true, for an undirected graph `g`, the matrix will contain arbitrary non-zero values representing connectivity between `v` and `i`.
