```
project(M::Grassmann, p)
```

Project `p` from the embedding onto the [`Grassmann`](@ref) `M`, i.e. compute `q` as the polar decomposition of $p$ such that $q^{\mathrm{H}}q$ is the identity, where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
