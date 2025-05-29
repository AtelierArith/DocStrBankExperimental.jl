```
get_vector(G::OrthogonalLieAlgebra, e, c, ::DefaultLieAlgebraOrthogonalBasis)
get_vector(G::SpecialOrthogonalLieAlgebra, e, c, ::DefaultLieAlgebraOrthogonalBasis)
get_vector!(G::OrthogonalLieAlgebra, X, e, c, ::DefaultLieAlgebraOrthogonalBasis)
get_vector!(G::SpecialOrthogonalLieAlgebra, X, e, c, ::DefaultLieAlgebraOrthogonalBasis)
```

接ベクトル $X ∈ 𝔬(n)$ を座標ベクトル $c ∈ ℝ^d$ に基づいて計算します。ここで、$d$ は [`OrthogonalGroup`](@ref) `O(n)` のリー代数の次元であり、座標は [`DefaultLieAlgebraOrthogonalBasis`](@ref) に関しています。これは [`hat`](@ref) で使用されるバージョンでもあります。

$$
O(2)
$$

の場合、係数は一つだけ ``$c = (α)^\mathrm{T}$ であり、したがって $X = \begin{pmatrix} 0 & -α\\ α & 0\end{pmatrix}$ が返されます。

$$
n=3
$$

の場合、通常の表現は $c = (α, β, γ)^\mathrm{T} ∈ ℝ^3$ を次のように変換します。

$$
    X = \begin{pmatrix} 0 & -γ & β\\ γ & 0 & -α\\ -β & α & 0\end{pmatrix},
$$

したがって、座標ベクトルは .

`n ≥ 4` の場合、すべての追加係数は下三角部分の次の行を埋めるために使用されます - これはスキュー対称性により上三角部分を決定します。
