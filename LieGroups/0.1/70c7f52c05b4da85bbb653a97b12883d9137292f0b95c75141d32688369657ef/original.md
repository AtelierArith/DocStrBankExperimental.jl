```
InverseRightGroupOperationAction <: AbstractLeftGroupActionType
```

A type for the [`AbstractLeftGroupActionType`](@ref) when acting on the group itself given by the inverse of a [`RightGroupOperationAction`](@ref) $σ_h$ as

$$
τ_h(g) \coloneqq σ_h^{-1}(g) = σ(h^{-1},g) = g∘h^{-1}
$$

Note that while in naming it is the inverse of the right action, it's properties yield that is is an [`AbstractLeftGroupActionType`](@ref), since

$$
τ_g(τ_h(p))
= σ^{\mathrm{R}}_{g^{-1}}(σ^{\mathrm{R}}_{h^{-1}}(p))
= σ^{\mathrm{R}}_{h^{-1}g^{-1}}(p)
= σ^{\mathrm{R}}_{(gh)^{-1}}(p)
τ_{gh}(p).
$$

for its inverse $(σ_h)^{-1}$ see [`InverseLeftGroupOperationAction`](@ref).
