```
project(M::GeneralizedGrassmann, p)
```

Project `p` from the embedding onto the [`GeneralizedGrassmann`](@ref) `M`, i.e. compute `q` as the polar decomposition of $p$ such that $q^{\mathrm{H}}Bq$ is the identity, where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transpose.
