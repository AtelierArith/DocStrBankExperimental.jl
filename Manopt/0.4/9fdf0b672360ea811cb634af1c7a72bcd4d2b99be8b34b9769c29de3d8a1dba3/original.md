```
y = get_differential_primal_prox(M::AbstractManifold, pdsno::PrimalDualManifoldSemismoothNewtonObjective σ, x)
get_differential_primal_prox!(p::TwoManifoldProblem, y, σ, x)
```

Evaluate the differential proximal map of $F$ stored within [`AbstractPrimalDualManifoldObjective`](@ref)

$$
D\operatorname{prox}_{σF}(x)[X]
$$

which can also be computed in place of `y`.
