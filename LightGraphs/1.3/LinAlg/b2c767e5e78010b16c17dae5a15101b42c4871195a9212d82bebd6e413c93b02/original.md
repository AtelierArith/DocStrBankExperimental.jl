```
adjacency_spectrum(g[, T=Int; dir=:unspec])
```

Return the eigenvalues of the adjacency matrix for a graph `g`, indexed by vertex. Default values for `T` are the same as those in [`adjacency_matrix`](@ref).

### Optional Arguments

`dir=:unspec`: Options for `dir` are the same as those in [`laplacian_matrix`](@ref).

### Performance

Converts the matrix to dense with $nv^2$ memory usage.

### Implementation Notes

Use `eigs(adjacency_matrix(g);  kwargs...)` to compute some of the eigenvalues/eigenvectors.
