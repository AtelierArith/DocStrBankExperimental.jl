```
GeneralizedPCAcor{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Scale-invariant principal component analysis (PCAcor) whitening transform, generalized to support compression based on either

1. a pre-determined number of components,
2. a fraction of the total squared cross-correlation, or
3. a relative tolerance on the number of eigenvalues greater than `rtol*λ₁` where `λ₁` is the largest eigenvalue of the correlation matrix.

Given the eigendecomposition of the $n × n$ correlation matrix, $P = GΘGᵀ$, with eigenvalues sorted in descending order, i.e. $θ₁ ≥ θ₂ ⋯ ≥ θₙ$, the first $m$ components are selected according to one or more of the criteria listed above.

If $m = n$, then we have the canonical PCA-cor whitening matrix,  $W = Θ^{-\frac{1}{2}}GᵀV^{-\frac{1}{2}}$. Otherwise, for $m < n$, a map from $ℝⁿ ↦ ℝᵐ$ is formed by removing the $n - m$ rows from $W$, i.e. the components with the $n - m$ smallest eigenvalues are removed. This is equivalent to selecting the $m × m$ matrix from the upper left of $Θ$ and the $m × n$ matrix from the top of $Gᵀ$. The inverse transform is then formed by selecting the $n × m$ matrix from the left of $G$ and the same matrix from $Θ$.
