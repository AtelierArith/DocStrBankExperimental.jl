```
q = get_primal_prox(M::AbstractManifold, p::AbstractPrimalDualManifoldObjective, σ, p)
get_primal_prox!(M::AbstractManifold, p::AbstractPrimalDualManifoldObjective, q, σ, p)
```

$$
F
$$

を[`AbstractPrimalDualManifoldObjective`](@ref)内に格納された近接写像を評価します。

$$
\operatorname{prox}_{σF}(x)
$$

これは`y`の代わりに計算することもできます。
