```
project(M::Stiefel,p)
```

Projects `p` from the embedding onto the [`Stiefel`](@ref) `M`, i.e. compute `q` as the polar decomposition of $p$ such that $q^{\mathrm{H}}q$ is the identity, where $⋅^{\mathrm{H}}$ denotes the hermitian, i.e. complex conjugate transposed.
