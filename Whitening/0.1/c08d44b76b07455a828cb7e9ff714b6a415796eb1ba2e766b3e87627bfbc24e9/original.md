```
PCAcor{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Scale-invariant principal component analysis (PCA-cor) whitening transform.

Given the eigendecomposition of the correlation matrix, $P = GΘGᵀ$, and the diagonal variance matrix, $V$, we have the whitening matrix, $W = Θ^{-\frac{1}{2}}GᵀV^{-\frac{1}{2}}$.
