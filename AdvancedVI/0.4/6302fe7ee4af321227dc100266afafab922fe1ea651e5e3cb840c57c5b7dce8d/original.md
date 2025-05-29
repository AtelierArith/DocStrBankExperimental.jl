```
MeanFieldGaussian(μ, L)
```

Construct a Gaussian variational approximation with a diagonal covariance matrix.

# Arguments

  * `μ::AbstractVector{T}`: Mean of the Gaussian.
  * `L::Diagonal{T}`: Diagonal Cholesky factor of the covariance of the Gaussian.
