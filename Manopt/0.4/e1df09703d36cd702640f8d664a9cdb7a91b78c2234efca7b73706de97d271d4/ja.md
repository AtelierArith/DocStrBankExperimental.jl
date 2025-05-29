```
η = get_differential_dual_prox(N::AbstractManifold, pdsno::PrimalDualManifoldSemismoothNewtonObjective, n, τ, X, ξ)
get_differential_dual_prox!(N::AbstractManifold, pdsno::PrimalDualManifoldSemismoothNewtonObjective, η, n, τ, X, ξ)
```

$$
G_n^*
$$

に格納された微分近接写像を評価します [`PrimalDualManifoldSemismoothNewtonObjective`](@ref)

$$
D\operatorname{prox}_{τG_n^*}(X)[ξ]
$$

これは`η`の代わりに計算することもできます。
