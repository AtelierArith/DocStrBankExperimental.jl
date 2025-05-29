```
MvNormalMeanCovariance{T <: Real, M <: AbstractVector{T}, P <: AbstractMatrix{T}} <: AbstractMvNormal
```

A multivariate normal distribution with mean `μ` and covariance matrix `Σ`, where `T` is the element type of the vectors `M` and matrices `P`.

# Fields

  * `μ::M`: The mean vector of the multivariate normal distribution.
  * `Σ::P`: The covariance matrix of the multivariate normal distribution
