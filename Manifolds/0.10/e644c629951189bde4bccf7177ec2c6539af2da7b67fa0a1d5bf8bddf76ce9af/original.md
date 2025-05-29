```
change_representer(M::MetricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, E::EuclideanMetric, p, X)
```

Given a tangent vector $X ∈ T_p\mathcal M$ representing a linear function on the tangent space at `p` with respect to the [`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`) `g_E`, this is turned into the representer with respect to the (default) metric, the [`GeneralizedBuresWassersteinMetric`](@ref) on the [`SymmetricPositiveDefinite`](@ref) `M`.

To be precise we are looking for $Z∈T_p\mathcal P(n)$ such that for all $Y∈T_p\mathcal P(n)$ it holds

$$
⟨X,Y⟩ = \operatorname{tr}(XY) = ⟨Z,Y⟩_{\mathrm{BW}}
$$

for all $Y$ and hence we get $Z = 2pXM + 2MXp$.
