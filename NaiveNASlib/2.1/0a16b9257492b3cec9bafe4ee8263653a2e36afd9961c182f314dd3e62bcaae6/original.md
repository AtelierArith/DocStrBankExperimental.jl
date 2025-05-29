```
Δsize!([utilityfun], [s::AbstractΔSizeStrategy], g::CompGraph)
Δsize!([utilityfun], [s::AbstractΔSizeStrategy], v::AbstractVertex)
```

Change size of (potentially) all vertices of graph `g` (or graph to which `v` is connected) according to the provided  [`AbstractΔSizeStrategy`](@ref) (default [`UpperInsertBound`](@ref)).

Return true of operation was successful, false otherwise.

Argument `utilityfun` provides a vector `utility = utilityfun(vx)` for any vertex `vx` in the same graph as `v` where  `utility[i] > utility[j]` indicates that output neuron index `i` shall be preferred over `j` for vertex `vx`. It may  also provide a scalar which will be used as utility of all neurons of `vx`. If not provided, [`defaultutility(vx)`](@ref) will be used.
