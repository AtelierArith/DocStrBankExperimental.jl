```
get_coordinates(𝔤::OrthogonalLieAlgebra, X, ::DefaultLieAlgebraOrthogonalBasis)
get_coordinates(G::SpecialOrthogonalLieAlgebra, X, ::DefaultLieAlgebraOrthogonalBasis)
get_coordinates!(G::OrthogonalLieAlgebra, c, X ::DefaultLieAlgebraOrthogonalBasis)
get_coordinates!(G::SpecialOrthogonalLieAlgebra, c, X ::DefaultLieAlgebraOrthogonalBasis)
```

リー代数接ベクトル $X ∈ 𝔬(n)$ から座標ベクトル $c ∈ ℝ^d$ を計算します。ここで、[`OrthogonalGroup`](@ref) `O(n)` の [`DefaultLieAlgebraOrthogonalBasis`](@ref) における $d$ はリー代数の次元です。これはまた、[`vee`](@ref) で使用されるバージョンでもあります。

$$
O(2)
$$

の場合、基底 $\begin{pmatrix} 0 & -α\\ α & 0\end{pmatrix}$ には係数 $α$ が1つだけあり、これは $c = (α)^\mathrm{T}$ として返されます。

$𝔬(3)$ の通常の基底表現は次のように与えられます。

$$
    X = \begin{pmatrix} 0 & -γ & β\\ γ & 0 & -α\\ -β & α & 0\end{pmatrix},
$$

したがって、座標ベクトルは $c = (α, β, γ)^\mathrm{T} ∈ ℝ^3$ です。

`n ≥ 4` の場合、下三角部分が $c$ に行単位で追加されます。
