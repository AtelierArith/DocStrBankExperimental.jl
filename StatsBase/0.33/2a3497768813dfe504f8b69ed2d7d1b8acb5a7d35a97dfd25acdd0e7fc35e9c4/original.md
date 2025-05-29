```
cov(ce::CovarianceEstimator, X::AbstractMatrix, [w::AbstractWeights]; mean=nothing, dims::Int=1)
```

Compute the covariance matrix of the matrix `X` along dimension `dims` using estimator `ce`. A weighting vector `w` can be specified. The keyword argument `mean` can be:

  * `nothing` (default) in which case the mean is estimated and subtracted from the data `X`,
  * a precalculated mean in which case it is subtracted from the data `X`. Assuming `size(X)` is `(N,M)`, `mean` can either be:

      * when `dims=1`, an `AbstractMatrix` of size `(1,M)`,
      * when `dims=2`, an `AbstractVector` of length `N` or an `AbstractMatrix` of size `(N,1)`.
