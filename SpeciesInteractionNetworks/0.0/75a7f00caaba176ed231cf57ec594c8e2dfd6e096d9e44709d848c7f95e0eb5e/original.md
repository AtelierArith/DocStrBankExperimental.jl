```
mangalnetwork(MN::Mangal.MangalNetwork, query::Pair...; taxonlevel::Bool=false)
```

Retrieves a network from [mangal.io](https://mangal.io), using the `Mangal.jl` API wrapper. The keyword argument `taxonlevel` specifies whether the original *node* or its *reference taxon* must be used. Note that not all nodes have an unambiguously attached reference taxon.

The networks are *always* returned as quantitative unipartite networks, as this is the one format that will *not* result in loss of information. If you want to bring them to a different representation, you can use the [`render`](@ref) methods.

Note that you can alternatively use an ID or a network name as the first argument. If you want to do more complicated queries, you can import the `Mangal` package using

```
using SpeciesInteractionNetworks
import SpeciesInteractionNetworks.Mangal
```

###### References

[Poisot2016mangal](@citet*)
