```
centrality(::Type{EigenvectorCentrality}, N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions})
```

Eigencentrality, corrected so that the centralities in the network sum to one.

The eigenvector centrality is calculated using Von Mises iteration, starting from a random vector.

where A is the adjacency matrix of the graph, b is the vector of centralities, At each iteration, the vector is updated to be A×b/|A×b|, and |⋅| is the norm.

The number of iterations is determined by the variable `SpeciesInteractionNetworks.CENTRALITY_MAXITER`, and the algorithm usually converges rapidly.

###### References

[Landau1895Zur](@citet*)
