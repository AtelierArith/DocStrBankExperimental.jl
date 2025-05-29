```
Y = get_dual_prox(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, n, τ, X)
get_dual_prox!(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, Y, n, τ, X)
```

$$
g_n^*
$$

の近接写像を[`AbstractPrimalDualManifoldObjective`](@ref)内で評価します。

$$
  Y = \operatorname{prox}_{τG_n^*}(X)
$$

これは`Y`の代わりにインプレースで計算することもできます。
