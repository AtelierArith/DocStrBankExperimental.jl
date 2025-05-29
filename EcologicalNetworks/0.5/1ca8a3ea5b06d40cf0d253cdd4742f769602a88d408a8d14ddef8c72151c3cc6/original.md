```
ρ(N::T; varargs...) where {T <: BipartiteNetwork}
```

Bipartite version of the spectral radius. In practice, this casts the network into its unipartite representation, since the spectral radius only makes sense for square matrices.
