```
cov(estimator::WoodburyEstimator, X::AbstractMatrix, weights::FrequencyWeights...; dims::Int=1, mean=nothing, UsV=nothing)
```

Estimate the covariance matrix from the data matrix `X` using a "spiked" covariance model

```
Σ = σ²I + U * Λ * U',
```

where `U` is a low-rank matrix of eigenvectors and `Λ` is a diagonal matrix.

Reference:     Donoho, D.L., Gavish, M. and Johnstone, I.M., 2018.     Optimal shrinkage of eigenvalues in the spiked covariance model. Annals of statistics, 46(4), p.1742.

When `σ²` is not supplied in `estimator`, it is calculated from the residuals `X - X̂`, where `X̂` is the low-rank approximation of `X` used to generate `U` and `Λ`.

If `X` is too large to manipulate in memory, you can pass `UsV = (U, s, V)` (a truncated SVD of `X - mean(X; dims)`) and then `X` will only be used compute the dimensionality and number of observations. This requires that you specify `estimator.σ²`.
