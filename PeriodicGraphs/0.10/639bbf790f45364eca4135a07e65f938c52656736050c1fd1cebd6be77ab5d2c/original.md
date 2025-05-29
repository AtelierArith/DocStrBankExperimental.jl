```
slice_graph(g::PeriodicGraph{D}, remove::Union{SVector{N},NTuple{N}}) where {D,N}
```

Extract a `PeriodicGraph{D-N}` from `g` by removing all edges that have an offset `o` such that `!iszero(o[remove])` and shrinking the resulting offsets. In other words, remove the dimensions in `remove`.

To only remove the edges while keeping the same number of dimensions, use [`slice_graph(g, collect(remove))`](@ref slice_graph(g::PeriodicGraph{D}, remove::Vector{<:Integer}) where D)

`remove` is assumed to be sorted and to contain unique elements.

!!! warning
    No verification of the previous assumption will be performed.

