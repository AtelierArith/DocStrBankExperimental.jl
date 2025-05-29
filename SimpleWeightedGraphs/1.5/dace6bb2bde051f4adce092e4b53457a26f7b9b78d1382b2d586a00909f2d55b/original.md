```
Graphs.laplacian_matrix(g, T; dir)
```

Subtract the adjacency matrix to the degree matrix, both filled with element type `T` and considering edge direction `dir ∈ [:in, :out, :both]` (unlike in Graphs.jl, default is `:out`).
