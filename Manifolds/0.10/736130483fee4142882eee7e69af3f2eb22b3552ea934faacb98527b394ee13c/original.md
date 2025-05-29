```
exp(M::MetricManifold{SymmetricPositiveDefinite,LogCholeskyMetric}, p, X)
```

Compute the exponential map on the [`SymmetricPositiveDefinite`](@ref) `M` with [`LogCholeskyMetric`](@ref) from `p` into direction `X`. The formula reads

$$
\exp_p X = (\exp_y W)(\exp_y W)^\mathrm{T}
$$

where $\exp_xW$ is the exponential map on [`CholeskySpace`](@ref), $y$ is the Cholesky decomposition of $p$, $W = y(y^{-1}Xy^{-\mathrm{T}})_\frac{1}{2}$, and $(⋅)_\frac{1}{2}$ denotes the lower triangular matrix with the diagonal multiplied by $\frac{1}{2}$.
