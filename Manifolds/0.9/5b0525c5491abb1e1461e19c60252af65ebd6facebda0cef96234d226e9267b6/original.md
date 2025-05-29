```
log(M::MetricManifold{ℝ,<:SymmetricPositiveDefinite,LogCholeskyMetric}, p, q)
```

Compute the logarithmic map on [`SymmetricPositiveDefinite`](@ref) `M` with respect to the [`LogCholeskyMetric`](@ref) emanating from `p` to `q`. The formula can be adapted from the [`CholeskySpace`](@ref) as

$$
\log_p q = xW^{\mathrm{T}} + Wx^{\mathrm{T}},
$$

where $x$ is the cholesky factor of $p$ and $W=\log_x y$ for $y$ the cholesky factor of $q$ and the just mentioned logarithmic map is the one on [`CholeskySpace`](@ref).
