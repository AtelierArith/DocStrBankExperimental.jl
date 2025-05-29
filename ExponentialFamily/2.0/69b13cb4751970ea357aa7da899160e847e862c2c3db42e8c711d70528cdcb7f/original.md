```
MvNormalMeanScalePrecision{T <: Real, M <: AbstractVector{T}} <: AbstractMvNormal
```

A multivariate normal distribution with mean `μ` and scale parameter `γ` that scales the identity precision matrix.

# Type Parameters

  * `T`: The element type of the mean vector and scale parameter
  * `M`: The type of the mean vector, which must be a subtype of `AbstractVector{T}`

# Fields

  * `μ::M`: The mean vector of the multivariate normal distribution
  * `γ::T`: The scale parameter that scales the identity precision matrix

# Notes

The precision matrix of this distribution is `γ * I`, where `I` is the identity matrix. The covariance matrix is the inverse of the precision matrix, i.e., `(1/γ) * I`.
