```
project(M::GeneralizedGrassmann, p, X)
```

Project the `n`-by-`k` `X` onto the tangent space of `p` on the [`GeneralizedGrassmann`](@ref) `M`, which is computed by

$$
\operatorname{proj_p}(X) = X - pp^{\mathrm{H}}B^\mathrm{T}X,
$$

where $⋅^{\mathrm{H}}$ denotes the complex conjugate transposed or Hermitian and $⋅^{\mathrm{T}}$ the transpose.
