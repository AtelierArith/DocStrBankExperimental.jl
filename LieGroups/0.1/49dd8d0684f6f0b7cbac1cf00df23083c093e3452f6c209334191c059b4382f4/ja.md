```
SpecialEuclideanMatrixTangentVector <: AbstractLieAlgebraTangentVector
```

は、次の形式の行列によっていくつかの [`AbstractLieGroup`](@ref) 上の接ベクトルを表します。

$$
\begin{pmatrix} M & v\\ \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix} ∈ ℝ^{(n+1)×(n+1)},
\qquad M ∈ ℝ^{n×n}, v ∈ \mathcal T(n),
$$

ここで、$\mathbf{0}_n ∈ ℝ^n$ はゼロを含むベクトルを示します。

この接ベクトル自体はアフィン行列ではありませんが、アフィン群のリー代数に使用することができます。
