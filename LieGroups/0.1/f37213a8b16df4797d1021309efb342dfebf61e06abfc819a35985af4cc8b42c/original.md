```
SpecialEuclideanMatrixPoint <: AbstractLieGroupPoint
```

represent a point on some [`AbstractLieGroup`](@ref) by an [affine matrix](https://en.wikipedia.org/wiki/Affine_group#Matrix_representation).

$$
\begin{pmatrix} M & v\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix} ∈ ℝ^{(n+1)×(n+1)},
\qquad M ∈ ℝ^{n×n}, v ∈ \mathcal T(n),
$$

where $\mathbf{0}_n ∈ ℝ^n$ denotes the vector containing zeros.
