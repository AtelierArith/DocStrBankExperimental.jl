```
AbstractLeftGroupActionType <: AbstractGroupActionType
```

A type representing a (smooth) group action $σ: \mathcal G × \mathcal M → \mathcal M$ of a [`AbstractLieGroup`](@ref) $\mathcal G$ acting (from the left) on an [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$. with the following properties

1. $σ(\mathrm{e}, p) = p$ holds for all $p ∈ \mathcal M$
2. $σ(g, σ(h, p)) = σ(g∘h, p)$ holds for all $g,h ∈ \mathcal G$, $p ∈ \mathcal M$

where $∘$ denotes the group operation of the [`AbstractLieGroup`](@ref) $\mathcal G$. See also [HilgertNeeb:2012; Definition 9.1.11](@cite).

The type of action can be seen a bit better when writing the action as a family $σ_g(p)$: we obtain from the second property as

$$
  σ_g(σ_h(p)) = σ_{gh}(p)
$$

and see that $g$ appears on the left.

To emphasize the side the group operation is acting from, we sometimes write $σ^{\mathrm{L}}$. If the action is clear from context we write $σ(g, p) = g ⋅ p$.

One notable example of a left action is the inverse of an action of [`AbstractRightGroupActionType`](@ref) $σ^{\mathrm{R}}$, which is given by $τ_g = (σ^{\mathrm{R}}_g)^{-1} = σ^{\mathrm{R}}_{g^{-1}}$. We obtain

$$
τ_g(τ_h(p))
= σ^{\mathrm{R}}_{g^{-1}}(σ^{\mathrm{R}}_{h^{-1}}(p))
= σ^{\mathrm{R}}_{h^{-1}g^{-1}}(p)
= σ^{\mathrm{R}}_{(gh)^{-1}}(p)
τ_{gh}(p).
$$

!!! note
    In function definitions we follow the idea of the family of actions and use the order `(M, g, p)` in function signatures.

