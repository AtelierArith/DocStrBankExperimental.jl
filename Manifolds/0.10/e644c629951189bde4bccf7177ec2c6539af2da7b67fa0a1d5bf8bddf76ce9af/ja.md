```
change_representer(M::MetricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, E::EuclideanMetric, p, X)
```

接ベクトル $X ∈ T_p\mathcal M$ は、点 `p` における接空間での線形関数を表しており、[`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`) `g_E` に関して、この接ベクトルは（デフォルトの）計量である [`GeneralizedBuresWassersteinMetric`](@ref) に関する表現者に変換されます。`SymmetricPositiveDefinite`(@ref) `M` に対してです。

正確には、すべての $Y∈T_p\mathcal P(n)$ に対して次の条件を満たす $Z∈T_p\mathcal P(n)$ を探しています。

$$
⟨X,Y⟩ = \operatorname{tr}(XY) = ⟨Z,Y⟩_{\mathrm{BW}}
$$

すべての $Y$ に対して、したがって $Z = 2pXM + 2MXp$ となります。 ```
