```
CoordinateVectorialType{B<:AbstractBasis} <: AbstractVectorialType
```

制約の勾配が特定の基底に関してヤコビ行列として実装されていることを示す型であり、制約が $g: \mathcal M → ℝ^m$ として与えられる場合、基底 $\mathcal B$ の $T_p\mathcal M$ に関して、$p∈ \mathcal M$ でこれを次のように書くことができます。$J_g(p) = (c_1^{\mathrm{T}},…,c_m^{\mathrm{T}})^{\mathrm{T}} \in ℝ^{m,d}$、すなわち、この行列の各行 $c_i$ は、`get_coefficients(M, p, c, B)` が接ベクトル $\oepratorname{grad} g_i(p)$ であるような係数の集合です。

例えば $g_i(p) ∈ ℝ^m$ または $\operatorname{grad} g_i(p) ∈ T_p\mathcal M$、$i=1,…,m$。

# フィールド

  * `basis` デフォルトの表現を示す [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`)。
