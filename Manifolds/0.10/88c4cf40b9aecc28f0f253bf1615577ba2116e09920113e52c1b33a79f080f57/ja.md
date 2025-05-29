```
injectivity_radius(M::SymmetricPositiveDefinite[, p])
injectivity_radius(M::MetricManifold{SymmetricPositiveDefinite,AffineInvariantMetric}[, p])
injectivity_radius(M::MetricManifold{SymmetricPositiveDefinite,LogCholeskyMetric}[, p])
```

[`SymmetricPositiveDefinite`](@ref) の射影半径を返します。`M` は [`AffineInvariantMetric`](@ref) および [`LogCholeskyMetric`](@ref) に関してハダマール多様体であるため、射影半径は全体で $∞$ です。
