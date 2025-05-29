```
q = get_primal_prox(M::AbstractManifold, p::AbstractPrimalDualManifoldObjective, σ, p)
get_primal_prox!(M::AbstractManifold, p::AbstractPrimalDualManifoldObjective, q, σ, p)
```

Evaluate the proximal map of $F$ stored within [`AbstractPrimalDualManifoldObjective`](@ref)

$$
\operatorname{prox}_{σF}(x)
$$

which can also be computed in place of `y`.
