```
nullmodel(::Type{Connectance}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

Returns a probabilistic network under the null model that all interactions occurr with a probability equal to the network connectance, *i.e.* in a network with $L$ links, and $|T|$ species on the top and $|B|$ species on the bottom,

$P(i \rightarrow j) = \frac{L}{|T|\times |B|}$

Note that for [`Unipartite`](@ref) networks, $|T| = |B| = |S|$ (the two sides have the same number of species).

###### References

[Fortuna2006Habitat](@citet*)
