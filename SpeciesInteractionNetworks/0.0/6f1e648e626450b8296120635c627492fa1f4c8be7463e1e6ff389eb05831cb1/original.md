```
centrality(::Type{GeneralizedClosenessCentrality}, N::SpeciesInteractionNetwork{<:Unipartite, <:Binary}; α=0.1)
```

The generalized closeness centrality of a binary network ranges from the degree centrality (α is 0) to the number of reachable nodes (α=1).
