```
vee(𝔤::LieAlgebra, X)
vee!(𝔤::LieAlgebra, c, X)
```

接続ベクトル `X` を [`LieAlgebra`](@ref) \mathfrak g からその Lie algebra における [`DefaultLieAlgebraOrthogonalBasis`](@ref) 基底に関する座標にマッピングする vee マップ $(⋅){\vee}: \mathfrak g → \mathcal V$ を計算します。

$$
X = \sum_{i∈\mathcal I} c_iB_i,
$$

ここで、$\{ B_i \}_{i∈\mathcal I}$ は Lie algebra の基底であり、$\mathcal I$ は通常 $\mathcal I=\{ 1,\ldots,n \}$ である対応するインデックス集合です。したがって、$\mathcal V = ℝ^n$ です。

計算は `c` のインプレースで実行できます。`vee` の逆は [`hat`](@ref) です。技術的には、`vee` は [`get_coordinates`](@ref) の特定のケースであり、[`DefaultLieAlgebraOrthogonalBasis`](@ref) を使用して実装されています。
