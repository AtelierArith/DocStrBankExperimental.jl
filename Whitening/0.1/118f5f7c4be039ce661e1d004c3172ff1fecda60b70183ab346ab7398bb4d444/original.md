```
Chol{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Cholesky whitening transform.

Given the Cholesky decomposition of the inverse covariance matrix, $Σ⁻¹ = LLᵀ$, we have the whitening matrix, $W = Lᵀ$.
