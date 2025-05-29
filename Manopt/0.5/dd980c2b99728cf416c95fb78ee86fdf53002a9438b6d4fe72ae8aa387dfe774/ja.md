```
CoordinateVectorialType{B<:AbstractBasis} <: AbstractVectorialType
```

制約の勾配が特定の基底に関してヤコビ行列として実装されていることを示す型であり、ベクトル関数が $f: \mathcal M → ℝ^m$ であり、$p∈ \mathcal M$ において $T_p\mathcal M$ の基底 $\mathcal B$ を持つ場合、これは次のように書くことができます：$J_g(p) = (c_1^{\mathrm{T}},…,c_m^{\mathrm{T}})^{\mathrm{T}} \in ℝ^{m,d}$、すなわち、この行列の各行 $c_i$ は、`get_coefficients(M, p, c, B)` が例えば $g_i(p) ∈ ℝ^m$ または $\operatorname{grad} g_i(p) ∈ T_p\mathcal M$ に対する接ベクトル $\oepratorname{grad} g_i(p)$ となるような係数のセットです。$i=1,…,m$。

# フィールド

  * `basis` ヤコビアンが表現される基底を示す [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`)。

# コンストラクタ

```
CoordinateVectorialType(basis=DefaultOrthonormalBasis())
```
