```
MvNormalWishart{T, M <: AbstractArray{T}, V <: AbstractMatrix{T}, K <: Real, N <: Real} <: ContinuousMatrixDistribution
```

A multivariate normal-Wishart distribution, where `T` is the element type of the arrays `M` and matrices `V`, and `K` and `N` are real numbers. This distribution is a joint distribution of a multivariate normal random variable with mean `μ` and a Wishart-distributed random matrix with scale matrix `Ψ`, degrees of freedom `ν`, and the scalar `κ` as a scaling parameter.

# Fields

  * `μ::M`: The mean vector of the multivariate normal distribution.
  * `Ψ::V`: The scale matrix of the Wishart distribution.
  * `κ::K`: The scaling parameter of the Wishart distribution.
  * `ν::N`: The degrees of freedom of the Wishart distribution
