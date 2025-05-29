```
log(::MatricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, p, q)
```

Compute the logarithmic map on [`SymmetricPositiveDefinite`](@ref) with respect to the [`BuresWassersteinMetric`](@ref) given by

$$
    \log_p(q) = M(M^{-1}pM^{-1}q)^{\frac{1}{2}} + (qM^{-1}pM^{-1})^{\frac{1}{2}}M - 2 p.
$$
