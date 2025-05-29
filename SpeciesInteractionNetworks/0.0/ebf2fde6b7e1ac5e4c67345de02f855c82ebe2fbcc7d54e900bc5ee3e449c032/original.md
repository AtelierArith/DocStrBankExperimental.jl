```
subgraph(N::SpeciesInteractionNetwork{<:Bipartite{T}, <:Interactions}, top::Vector{T}, bottom::Vector{T}) where {T}
```

We can induce a subgraph from a biparite network by specifying two arrays for nodes to be included. Note that any array can instead be `:`, in which case the entire series of nodes for this side of the network is used.
