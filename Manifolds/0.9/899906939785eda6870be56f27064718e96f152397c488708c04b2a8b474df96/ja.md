```
project(M::Flag, p::OrthogonalPoint, X::OrthogonalTVector)
```

ベクトル `X` を [`Flag`](@ref) 多様体 `M` $\operatorname{Flag}(n_1, n_2, ..., n_d; N)$ の点 `p` での接空間に射影します。これはまず `X` を [`SkewHermitianMatrices`](@ref) の空間に射影し、その後対角ブロックを 0 に設定することで機能します：

$$
X = \begin{bmatrix}
0                     & B_{1,2}               & ⋯ & B_{1,d+1} \\
-B_{1,2}^\mathrm{T}   & 0                     & ⋯ & B_{2,d+1} \\
\vdots                & \vdots                & ⋱ & \vdots    \\
-B_{1,d+1}^\mathrm{T} & -B_{2,d+1}^\mathrm{T} & ⋯ & 0
\end{bmatrix}
$$

ここで $B_{i,j} ∈ ℝ^{(n_i - n_{i-1}) × (n_j - n_{j-1})}$,  $1 ≤ i < j ≤ d+1$ の場合です。
