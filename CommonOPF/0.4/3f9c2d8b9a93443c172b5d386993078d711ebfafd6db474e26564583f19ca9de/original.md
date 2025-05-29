```
phi_ij(j::String, net::Network, M::AbstractMatrix)
```

Down-select the matrix M by the phase from i -> j, storing `0im` in the missing off-diagonal phase indices and `0` in the diagonal missing indices.
