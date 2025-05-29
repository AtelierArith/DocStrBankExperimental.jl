```
Δsize!(s::AbstractΔSizeStrategy) 
Δsize!(utilityfun, s::AbstractΔSizeStrategy)
```

Change size of (potentially) all vertices which `s` has a chance to impact the size of.

Argument `utilityfun` provides a vector `utility = utilityfun(vx)` for any vertex `vx` in the same graph as `v` where  `utility[i] > utility[j]` indicates that output neuron index `i` shall be preferred over `j` for vertex `vx`. It may  also provide a scalar which will be used as utility of all neurons of `vx`. If not provided, [`defaultutility(vx)`](@ref) will be used.
