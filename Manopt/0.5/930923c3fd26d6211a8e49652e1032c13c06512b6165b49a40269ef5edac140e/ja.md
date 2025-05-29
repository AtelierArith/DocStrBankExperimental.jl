```
Y = get_dual_prox(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, n, τ, X)
get_dual_prox!(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, Y, n, τ, X)
```

$$
g_n^*
$$

が[`AbstractPrimalDualManifoldObjective`](@ref)内に格納されている近接写像を評価します。

$$
  Y = \operatorname{prox}}_{τG_n^*}(X)
$$

これは`Y`の代わりにインプレースで計算することもできます。
