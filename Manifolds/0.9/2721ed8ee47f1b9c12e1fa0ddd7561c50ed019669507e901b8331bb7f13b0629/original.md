```
project(M::GeneralizedStiefel, p)
```

Project `p` from the embedding onto the [`GeneralizedStiefel`](@ref) `M`, i.e. compute `q` as the polar decomposition of $p$ such that $q^{\mathrm{H}}Bq$ is the identity, where $⋅^{\mathrm{H}}$ denotes the hermitian, i.e. complex conjugate transposed.
