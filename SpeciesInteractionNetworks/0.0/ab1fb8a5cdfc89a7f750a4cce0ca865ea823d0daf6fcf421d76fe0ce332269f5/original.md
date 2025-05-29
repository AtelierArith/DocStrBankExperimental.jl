```
modularity(N::SpeciesInteractionNetwork{<:Partiteness[T], <:Binary}, L::Dict{T,Int}) where {T}
```

Modularity of a network and its partition. The second argument is a dictionary where every species of `N` is associated to an integer value representing the identity of the module. This function returns the same value for bipartite networks and their unipartite projection. This measure is usually called $Q$.

Note that in [Newman2006Modularity](@citet), the null model is corrected by $2m$, where $m$ is the number of links in the network. This is appropriate for *undirected* interactions, and so in the code we only divide by $m$. Note that this ensure that the modularity matrix has the correct property, *i.e.* its rows and columns sum to (approx.) 0.

###### References

[Barber2007Modularity](@citet*)

[Newman2006Modularity](@citet*)
