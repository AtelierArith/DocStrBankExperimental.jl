```
injectivity_radius(M::SymmetricPositiveDefinite[, p])
injectivity_radius(M::MetricManifold{SymmetricPositiveDefinite,AffineInvariantMetric}[, p])
injectivity_radius(M::MetricManifold{SymmetricPositiveDefinite,LogCholeskyMetric}[, p])
```

Return the injectivity radius of the [`SymmetricPositiveDefinite`](@ref). Since `M` is a Hadamard manifold with respect to the [`AffineInvariantMetric`](@ref) and the [`LogCholeskyMetric`](@ref), the injectivity radius is globally $∞$.
