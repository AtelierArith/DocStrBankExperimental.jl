```
PCA{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Principal component analysis (PCA) whitening transform.

Given the eigendecomposition of the covariance matrix, $Σ = UΛUᵀ$, we have the whitening matrix, $W = Λ^{-\frac{1}{2}}Uᵀ$.
