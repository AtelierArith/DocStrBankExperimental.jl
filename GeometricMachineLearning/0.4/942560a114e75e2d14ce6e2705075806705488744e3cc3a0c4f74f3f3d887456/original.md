```
MomentumOptimizer(η, α)
```

Make an instance of the momentum optimizer.

The momentum optimizer is similar to the [`GradientOptimizer`](@ref). It however has a nontrivial cache that stores past history (see [`MomentumCache`](@ref)). The cache is updated via:

$$
    B^{\mathrm{cache}} \gets \alpha{}B^{\mathrm{cache}} + \nabla_\mathrm{weights}L
$$

and then the final velocity is computed as

$$
    \mathrm{velocity} \gets  - \eta{}B^{\mathrm{cache}}.
$$

# Implementation

To save memory the *velocity* is stored in the input $\nabla_WL$. This is similar to the case of the [`GradientOptimizer`](@ref).
