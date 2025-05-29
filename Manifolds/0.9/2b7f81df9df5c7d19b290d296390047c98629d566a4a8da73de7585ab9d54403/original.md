```
project(M::Grassmann, p, X)
```

Project the `n`-by-`k` `X` onto the tangent space of `p` on the [`Grassmann`](@ref) `M`, which is computed by

$$
\operatorname{proj_p}(X) = X - pp^{\mathrm{H}}X,
$$

where $⋅^{\mathrm{H}}$ denotes the complex conjugate transposed or Hermitian.
