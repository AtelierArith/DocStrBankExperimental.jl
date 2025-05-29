```
log(M::SymmetricPositiveDefinite, p, q)
log(M::MetricManifold{SymmetricPositiveDefinite,AffineInvariantMetric}, p, q)
```

Compute the logarithmic map from `p` to `q` on the [`SymmetricPositiveDefinite`](@ref) as a [`MetricManifold`](@ref) with [`AffineInvariantMetric`](@ref). The formula reads

$$
\log_p q =
p^{\frac{1}{2}}\operatorname{Log}(p^{-\frac{1}{2}}qp^{-\frac{1}{2}})p^{\frac{1}{2}},
$$

where $\operatorname{Log}$ denotes to the matrix logarithm.
