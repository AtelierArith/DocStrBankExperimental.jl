```
FullRankGaussian(μ, L)
```

Construct a Gaussian variational approximation with a dense covariance matrix.

# Arguments

  * `μ::AbstractVector{T}`: Mean of the Gaussian.
  * `L::LinearAlgebra.AbstractTriangular{T}`: Cholesky factor of the covariance of the Gaussian.
