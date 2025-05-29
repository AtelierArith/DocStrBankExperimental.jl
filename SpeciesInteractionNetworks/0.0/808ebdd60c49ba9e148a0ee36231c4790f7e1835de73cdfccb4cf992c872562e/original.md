```
simplify(N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions}, allow_self_interactions::Bool=true)
```

Returns a *copy* of a network containing only the species with interactions. Internally, this calls [`isdisconnected`](@ref) – see this documentation for the consequences of `allow_self_interactions`.
