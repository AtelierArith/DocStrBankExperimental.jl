```
InverseLeftGroupOperationAction <: AbstractRightGroupActionType
```

A type for the [`AbstractLeftGroupActionType`](@ref) when acting on the group itself given by the inverse of a [`LeftGroupOperationAction`](@ref) $σ_h$ as

$$
τ_h(g) \coloneqq σ_h^{-1}(g) = σ(h^{-1},g) = h^{-1}∘g
$$

Note that while in naming it is the inverse of the left action, it's properties yield that is is an [`AbstractRightGroupActionType`](@ref), since

$$
τ_g(τ_h(p))
= σ^{\mathrm{L}}_{g^{-1}}(σ^{\mathrm{L}}_{h^{-1}}(p))
= σ^{\mathrm{L}}_{g^{-1}h^{-1}}(p)
= σ^{\mathrm{L}}_{(hg)^{-1}}(p)
τ_{hg}(p).
$$

for its inverse $(σ_h)^{-1}$ see [`InverseLeftGroupOperationAction`](@ref).

!!! note
    Some literature also calls this by itself *the* right group operation action.

