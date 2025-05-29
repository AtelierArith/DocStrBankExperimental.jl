```
laplacian_matrix(g, dir::Symbol=:out, T::DataType=Int)
```

Returns a sparse [Laplacian matrix](https://en.wikipedia.org/wiki/Laplacian_matrix) for a graph `g`, indexed by `[u, v]` vertices. `dir` has to be `:in, :out` or `:all`.
