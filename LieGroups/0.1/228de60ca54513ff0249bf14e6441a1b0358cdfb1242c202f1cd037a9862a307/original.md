```
GroupAction{T<:GroupActionType, L<:LieGroup, M<:AbstractManifold}
```

Specify a group action of [`AbstractGroupActionType`](@ref) `T` of a [`AbstractLieGroup`](@ref) `G` acting on `M`.

Let $\mathcal M$ be a [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) and $\mathcal G$ be a [`AbstractLieGroup`](@ref) with group operation $∘$.

A (smooth) action of the group $\mathcal G$ on the manifold $\mathcal M$ is a map

$$
σ: \mathcal G × \mathcal M → \mathcal M
$$

with the properties

  * $σ(\mathrm{e}, p) = p$ holds for all $p ∈ \mathcal M$
  * $σ(g, σ(h, p)) = σ(g∘h, p)$ holds for all $g,h ∈ \mathcal G$, $p ∈ \mathcal M$

# Fields

  * `type::T`: The type of the group action.
  * `group::L`: The group acting.
  * `manifold::M`: The manifold the group acts upon.

See [HilgertNeeb:2012; Section 9.1.3](@cite) for more details.
