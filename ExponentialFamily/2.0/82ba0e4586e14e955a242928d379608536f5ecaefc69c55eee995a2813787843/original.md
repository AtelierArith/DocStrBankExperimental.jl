```
MvNormalWeightedMeanPrecision{T <: Real, M <: AbstractVector{T}, P <: AbstractMatrix{T}} <: AbstractMvNormal
```

A multivariate normal distribution with a weighted mean vector `xi` and precision matrix `Λ`, where `T` is the element type of the vectors `M` and matrices `P`. This struct represents a natural parametrization of a multivariate Gaussian distribution.

# Fields

  * `xi::M`: The weighted mean vector of the multivariate normal distribution.
  * `Λ::P`: The precision matrix (inverse of the covariance matrix) of the multivariate normal distribution.
