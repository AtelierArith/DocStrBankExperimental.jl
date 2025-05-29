```
isdisconnected(N::SpeciesInteractionNetwork{Unipartite{T}, <:Interactions}, sp::T, allow_self_interactions::Bool=true) where {T}
```

Returns `true` if the species has no interaction; the last argument (`allow_self_interactions`, defaults to `true`) indicates whether self-interactions are allowed. If `false`, species that only interact with themselves are considered to be disconnected.
