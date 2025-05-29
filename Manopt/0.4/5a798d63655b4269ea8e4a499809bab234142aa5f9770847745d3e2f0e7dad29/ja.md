```
q = get_primal_prox(M::AbstractManifold, p::AbstractPrimalDualManifoldObjective, σ, p)
get_primal_prox!(M::AbstractManifold, p::AbstractPrimalDualManifoldObjective, q, σ, p)
```

[`AbstractPrimalDualManifoldObjective`](@ref) に格納されている $F$ の近接写像を評価します。

$$
\operatorname{prox}_{σF}(x)
$$

これは `y` の代わりに計算することもできます。
