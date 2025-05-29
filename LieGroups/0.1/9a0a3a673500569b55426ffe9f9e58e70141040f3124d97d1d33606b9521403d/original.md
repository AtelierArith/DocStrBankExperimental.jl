```
RightSemidirectProductLieGroup(
    N::LieGroup, H::LieGroup, action::AbstractGroupActionType=default_right_action(N,H)
)
```

Generate the semidirect product Lie Group $\mathcal G = N ⋊ H$ for an [`AbstractLeftGroupActionType`](@ref) using the [`RightSemidirectProductGroupOperation`](@ref) for the group operation definition as well as [HilgertNeeb:2012; Definition 9.2.22](@cite), first definition, for more details.

The short form `N`[`⋊`](@ref ⋊(L1::LieGroup, L2::LieGroup))`H` can be used if the corresponding [`default_right_action`](@ref)`(N,H)` is the one you want to use.
