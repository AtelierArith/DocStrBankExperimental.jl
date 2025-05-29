```
laplacian_matrix(g[, T=Int; dir=:unspec])
```

Return a sparse [Laplacian matrix](https://en.wikipedia.org/wiki/Laplacian_matrix) for a graph `g`, indexed by `[u, v]` vertices. `T` defaults to `Int` for both graph types.

### Optional Arguments

`dir=:unspec`: `:unspec`, `:both`, `:in`, and `:out` are currently supported. For undirected graphs, `dir` defaults to `:out`; for directed graphs, `dir` defaults to `:both`.
