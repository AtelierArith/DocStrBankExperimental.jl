```
centrality(::Type{ClosenessCentrality}, N::SpeciesInteractionNetwork{<:Unipartite, <:Probabilistic})
```

The closeness centrality of a probabilistic network is measured using the *random walk* closeness centrality, where the distance between two nodes i and j is measured as the first passage time on node j of a random walk starting on node i. This function does not look for shortest paths, and is therefore reasonably fast.
