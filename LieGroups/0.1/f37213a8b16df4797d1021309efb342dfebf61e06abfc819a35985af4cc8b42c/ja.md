```
SpecialEuclideanMatrixPoint <: AbstractLieGroupPoint
```

は、いくつかの [`AbstractLieGroup`](@ref) 上の点を [アフィン行列](https://en.wikipedia.org/wiki/Affine_group#Matrix_representation) によって表します。

$$
\begin{pmatrix} M & v\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix} ∈ ℝ^{(n+1)×(n+1)},
\qquad M ∈ ℝ^{n×n}, v ∈ \mathcal T(n),
$$

ここで、$\mathbf{0}_n ∈ ℝ^n$ はゼロを含むベクトルを示します。
