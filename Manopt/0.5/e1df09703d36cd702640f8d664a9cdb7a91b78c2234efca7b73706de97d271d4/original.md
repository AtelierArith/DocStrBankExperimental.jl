```
η = get_differential_dual_prox(N::AbstractManifold, pdsno::PrimalDualManifoldSemismoothNewtonObjective, n, τ, X, ξ)
get_differential_dual_prox!(N::AbstractManifold, pdsno::PrimalDualManifoldSemismoothNewtonObjective, η, n, τ, X, ξ)
```

Evaluate the differential proximal map of $G_n^*$ stored within [`PrimalDualManifoldSemismoothNewtonObjective`](@ref)

$$
D\operatorname{prox}_{τG_n^*}(X)[ξ]
$$

which can also be computed in place of `η`.
