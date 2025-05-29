```
isdegenerate(N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions}, allow_self_interactions::Bool=true)
```

A unipartite network is degenerate if it has species with no interactions. In some cases, it is useful to consider that a species with only self-interactions is disconnected from the network – this can be done by using `false` as the second argument (the default is to *allow* species with only self interactions to remain).
