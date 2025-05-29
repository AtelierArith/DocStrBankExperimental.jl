```
PeriodicGraph{D}(graph::PeriodicGraph{N}) where {D,N}
```

Return a graph that has the same structural information as the input `graph` but embedded in `D` dimensions instead of `N`. It will fail if the dimensionality of the graph is greater than `D`.

!!! note
    The behaviour is undefined if `D < N` and there are multiple non-identical connected components. In particular, the function is expected to fail if these components do not share the same orientation.

