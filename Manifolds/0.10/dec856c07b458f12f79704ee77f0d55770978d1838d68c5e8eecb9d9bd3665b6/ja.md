```
change_representer(M::SymmetricPositiveDefinite, E::EuclideanMetric, p, X)
```

接触ベクトル $X ∈ T_p\mathcal M$ は、点 `p` における接空間に対する線形関数を表しており、[`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`) `g_E` に関して、これを（デフォルトの）計量である [`AffineInvariantMetric`](@ref) に関する表現者に変換します。 [`SymmetricPositiveDefinite`](@ref) `M`。

正確には、すべての $Y∈T_p\mathcal P(n)$ に対して次が成り立つ $Z∈T_p\mathcal P(n)$ を探しています。

$$
⟨X,Y⟩ = \operatorname{tr}(XY) = \operatorname{tr}(p^{-1}Zp^{-1}Y) = g_p(Z,Y)
$$

したがって、$Z = pXp$ です。
