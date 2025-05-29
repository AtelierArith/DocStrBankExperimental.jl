```
GeneralizedPCA{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Principal component analysis (PCA) whitening transform, generalized to support compression based on either

1. a pre-determined number of components,
2. a fraction of the total squared cross-covariance, or
3. a relative tolerance on the number of eigenvalues greater than `rtol*λ₁` where `λ₁` is the largest eigenvalue of the covariance matrix.

Given the eigendecomposition of the $n × n$ covariance matrix, $Σ = UΛUᵀ$, with eigenvalues sorted in descending order, i.e. $λ₁ ≥ λ₂ ⋯ ≥ λₙ$, the first $m$ components are selected according to one or more of the criteria listed above.

If $m = n$, then we have the canonical PCA whitening matrix,  $W = Λ^{-\frac{1}{2}}Uᵀ$. Otherwise, for $m < n$, a map from $ℝⁿ ↦ ℝᵐ$ is formed by removing the $n - m$ rows from $W$, i.e. the components with the $n - m$ smallest eigenvalues are removed. This is equivalent to selecting the $m × m$ matrix from the upper left of $Λ$ and the $m × n$ matrix from the top of $Uᵀ$. The inverse transform is then formed by selecting the $n × m$ matrix from the left of $U$ and the same matrix from $Λ$.
