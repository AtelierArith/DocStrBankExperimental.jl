```
Δsize!([utilityfun], [s::AbstractΔSizeStrategy], vs::AbstractVector{<:AbstractVertex})
```

Change size of (potentially) all vertices in `vs` according to the provided [`AbstractΔSizeStrategy`](@ref) (default  [`UpperInsertBound`](@ref)).

Argument `utilityfun` provides a vector `utility = utilityfun(vx)` for any vertex `vx` in the same graph as `v` where  `utility[i] > utility[j]` indicates that output neuron index `i` shall be preferred over `j` for vertex `vx`. It may also provide a scalar which will be used as utility of all neurons of `vx`. If not provided, [`defaultutility(vx)`](@ref)  will be used.
