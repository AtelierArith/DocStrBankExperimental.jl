```
MvNormalMeanPrecision{T <: Real, M <: AbstractVector{T}, P <: AbstractMatrix{T}} <: AbstractMvNormal
```

A multivariate normal distribution with mean `μ` and precision matrix `Λ`, where `T` is the element type of the vectors `M` and matrices `P`.

# Fields

  * `μ::M`: The mean vector of the multivariate normal distribution.
  * `Λ::P`: The precision matrix (inverse of the covariance matrix) of the multivariate normal distribution.
