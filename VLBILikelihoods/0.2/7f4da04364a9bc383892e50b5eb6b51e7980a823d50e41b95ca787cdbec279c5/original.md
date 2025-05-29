```
ComplexVisLikelihood(μ::AbstractVector{<:Complex}, Σ::AbstractVector{<:Real})
```

Creates the complex visibility likelihood distribution which is a diagonal complex Gaussian with strictly real covariance matrix.

## Paramters

  * `μ`: The mean complex visibility, which is usually computed from some VLBI model
  * `Σ`: The measurement covariance matrix, which is usually computed directly from the data.      Note that `Σ` must be a real element vector and is interpreted at the diagonal of the      covariance matrix.
