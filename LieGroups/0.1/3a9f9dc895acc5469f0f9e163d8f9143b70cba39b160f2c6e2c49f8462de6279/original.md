```
LeftSemidirectProductLieGroup(
    N::LieGroup, H::LieGroup, action::AbstractGroupActionType=default_left_action(N, H)
)
```

Generate the semidirect product Lie Group $\mathcal G = N ⋉ H$ for an [`AbstractLeftGroupActionType`](@ref) using the [`LeftSemidirectProductGroupOperation`](@ref) for the group operation definition as well as [HilgertNeeb:2012; Definition 9.2.22](@cite), second definition, for more details.

The short form `N`[`⋉`](@ref ⋉(L1::LieGroup, L2::LieGroup))`H` can be used if the corresponding [`default_left_action`](@ref)`(N,H)` is the one you want to use.
