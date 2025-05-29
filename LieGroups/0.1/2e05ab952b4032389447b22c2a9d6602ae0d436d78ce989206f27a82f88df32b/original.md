```
AbstractRightGroupActionType <: AbstractGroupActionType
```

A type representing a (smooth) group action $σ: \mathcal M × \mathcal G → \mathcal M$ of a [`AbstractLieGroup`](@ref) $\mathcal G$ acting (from the right) on an [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$. with the following properties

1. $σ(p, \mathrm{e}) = p$ holds for all $p ∈ \mathcal M$
2. $σ(σ(p, g), h) = σ(p, g∘h)$ holds for all $g,h ∈ \mathcal G$, $p ∈ \mathcal M$

where $∘$ denotes the group operation of the [`AbstractLieGroup`](@ref) $\mathcal G$. See also [HilgertNeeb:2012; Remark 9.1.12](@cite).

The type of action can be seen a bit better when writing the action as a family $σ_g(p)$: we obtain from the second property as

$$
  σ_g(σ_h(p)) = σ_{hg}(p)
$$

and see that $g$ appears on the right.

To emphasize the side the group operation is acting from, we sometimes write $σ^{\mathrm{R}}$. If the action is clear from context we write $σ(p, g) = p ⋅ g$.

One notable example of a right action is the inverse of an action of  [`AbstractLeftGroupActionType`](@ref) $σ^{\mathrm{L}}$, which is given by $τ_g = (σ^{\mathrm{L}}_g)^{-1} = σ^{\mathrm{L}}_{g^{-1}}$. We obtain

$$
τ_g(τ_h(p))
= σ^{\mathrm{L}}_{g^{-1}}(σ^{\mathrm{L}}_{h^{-1}}(p))
= σ^{\mathrm{L}}_{g^{-1}h^{-1}}(p)
= σ^{\mathrm{L}}_{(hg)^{-1}}(p)
τ_{hg}(p).
$$

!!! note
    In function definitions we follow the idea of the family of actions and use the order `(M, g, p)` in function signatures.

