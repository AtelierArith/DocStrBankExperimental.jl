```
Y = get_dual_prox(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, n, τ, X)
get_dual_prox!(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, Y, n, τ, X)
```

Evaluate the proximal map of $g_n^*$ stored within [`AbstractPrimalDualManifoldObjective`](@ref)

$$
  Y = \operatorname{prox}_{τG_n^*}(X)
$$

which can also be computed in place of `Y`.
