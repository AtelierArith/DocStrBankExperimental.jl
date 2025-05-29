```
log(::MatricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, p, q)
```

[`SymmetricPositiveDefinite`](@ref) に関して、[`BuresWassersteinMetric`](@ref) による対数写像を計算します。

$$
    \log_p(q) = M(M^{-1}pM^{-1}q)^{\frac{1}{2}} + (qM^{-1}pM^{-1})^{\frac{1}{2}}M - 2 p.
$$
