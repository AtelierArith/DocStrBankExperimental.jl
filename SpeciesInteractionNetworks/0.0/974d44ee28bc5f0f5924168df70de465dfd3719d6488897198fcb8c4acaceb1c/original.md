```
SpeciesInteractionNetwork{P<:Partiteness, E<:Interactions}
```

A `SpeciesInteractionNetwork` type represents a species interaction network.

This type has two fields: `nodes` (a `Partiteness`), and `edges` (an `Interactions`). Because these two types are parametric, we can learn everything there is to know about the data structure in a network by looking at the type alone.

For example, a bipartite quantitative network where species are symbols and interactions are 32-bits floating point numbers will have the type

```
SpeciesInteractionNetwork{Bipartite{Symbol}, Interactions{Float32}}
```

This enables very specialized dispatch and indexing thoughout the package.
