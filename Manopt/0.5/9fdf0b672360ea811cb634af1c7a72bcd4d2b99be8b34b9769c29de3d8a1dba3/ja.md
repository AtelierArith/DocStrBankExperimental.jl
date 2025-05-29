```
y = get_differential_primal_prox(M::AbstractManifold, pdsno::PrimalDualManifoldSemismoothNewtonObjective σ, x)
get_differential_primal_prox!(p::TwoManifoldProblem, y, σ, x)
```

$$
F
$$

の微分近接写像を評価します [`AbstractPrimalDualManifoldObjective`](@ref)

$$
D\operatorname{prox}_{σF}(x)[X]
$$

これは`y`の代わりに計算することもできます。
