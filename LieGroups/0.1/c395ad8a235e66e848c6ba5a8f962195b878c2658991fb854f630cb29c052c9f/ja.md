```
hat(G::LieAlgebra, c)
hat(G::LieAlgebra, c, T::Type)
hat!(G::LieAlgebra, X::T, c)
```

ベクトルの座標 $\mathbf{c} ∈ \mathcal V$ を接ベクトル $X ∈ \mathfrak g$ にマッピングするハット写像 $(⋅)^{\wedge}: \mathcal V → 𝔤$ を計算します。係数は、リー代数の接ベクトルに対する特定の基底に関して与えられます。

$$
X = \sum_{i∈\mathcal I} c_iB_i,
$$

ここで、$\{ B_i \}_{i∈\mathcal I}$ はリー代数の基底であり、$\mathcal I$ は通常 $\mathcal I=\{ 1,\ldots,n \}$ である対応するインデックス集合です。したがって、$\mathcal V = ℝ^n$ です。

割り当てバリアントでは、異なる表現がある場合に接ベクトルの型 `T` を指定できます。最初のシグネチャはデフォルトの表現を生成します。

計算は `X` のインプレースで実行できます。`hat` の逆は [`vee`](@ref) です。技術的には、`hat` は [`get_vector`](@ref) の特定のケースであり、[`DefaultLieAlgebraOrthogonalBasis`](@ref) を使用して実装されています。
