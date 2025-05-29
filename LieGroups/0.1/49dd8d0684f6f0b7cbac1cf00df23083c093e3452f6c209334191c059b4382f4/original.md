```
SpecialEuclideanMatrixTangentVector <: AbstractLieAlgebraTangentVector
```

represent a tangent vector on some [`AbstractLieGroup`](@ref) by a matrix of the form

$$
\begin{pmatrix} M & v\\ \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix} ∈ ℝ^{(n+1)×(n+1)},
\qquad M ∈ ℝ^{n×n}, v ∈ \mathcal T(n),
$$

where $\mathbf{0}_n ∈ ℝ^n$ denotes the vector containing zeros.

While this tangent vector itself is not an affine matrix itself, it can be used for the Lie algebra of the affine group
