```
map_simple_wmis(graph::SimpleGraph, weights::AbstractVector) -> WMISResult
```

Map a weighted MIS problem to a weighted MIS problem on a defected King's graph.

!!! note
    The input coupling strength and onsite energies must be << 1. This method does not provide path decomposition based optimization, check [`map_graph`](@ref) for the path decomposition optimized version.

