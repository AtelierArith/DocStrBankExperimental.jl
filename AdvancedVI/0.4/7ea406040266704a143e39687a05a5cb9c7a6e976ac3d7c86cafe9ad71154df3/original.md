```
LowRankGaussian(μ, D, U)
```

Construct a Gaussian variational approximation with a diagonal plus low-rank covariance matrix.

# Arguments

  * `μ::AbstractVector{T}`: Mean of the Gaussian.
  * `D::Vector{T}`: Diagonal of the scale.
  * `U::Matrix{T}`: Low-rank factors of the scale, where `size(U,2)` is the rank.
