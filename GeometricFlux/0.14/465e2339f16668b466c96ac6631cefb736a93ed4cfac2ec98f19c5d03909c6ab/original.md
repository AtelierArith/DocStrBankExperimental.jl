```
positional_encode(LaplacianPE{K}, A)
```

Returns positional encoding (PE) of size `(K, N)` where `N` is node number. PE is generated from eigenvectors of a graph Laplacian truncated by `K`.

# Arguments

  * `K::Int`: First dimension of PE.
  * `A`: Adjacency matrix of a graph.

See also [`LaplacianPE`](@ref) for graph Laplacian method.
