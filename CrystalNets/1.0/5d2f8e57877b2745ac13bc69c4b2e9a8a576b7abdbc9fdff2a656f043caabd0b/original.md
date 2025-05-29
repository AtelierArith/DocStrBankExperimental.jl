```
topological_genome(net::CrystalNet{D,T})::String where {D,T}
```

Compute the topological genome of a net. The topological genome is an invariant if the net, meaning that it does not depend on its representation. It is also the string representation of a D-periodic graph such that `PeriodicGraph{D}(topological_genome(net))` is isomorphic to `net.pge.g` (except possibly if the `ignore_types` option is unset).

Return a [`TopologicalGenome`](@ref).

!!! info
    Options must be passed directly within `net`.

