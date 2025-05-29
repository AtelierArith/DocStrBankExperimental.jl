```
centrality(::Type{KatzCentrality}, N::SpeciesInteractionNetwork{<:Unipartite, <:Union{Binary, Probabilistic}}; α::AbstractFloat=0.1)
```

This measure gives a different weight to every subsequent connection (`α`). `α` is a weight, specifically the attenuation of each subsequent move away from the node, and therefore must be positive.

Note that internally, this function uses linear algebra shortcuts (rather than a sum over path lengths) to calculate the centrality, which is faster. As a consequence, there is, for each network, a maximal value of α that is the reciprocal of the absolute value of the leading eigenvalue of the adjacency matrix. This α has no analytical solution when the adjacency matrix has complex eigenvalues. It is recommended to use this centrality algorithm as part of a `try`/`catch` block if using large values of α.

###### References

[Junker2008Analysis](@citet*)
