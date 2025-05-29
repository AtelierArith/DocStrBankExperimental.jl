```
slice_graph(g::PeriodicGraph{D}, remove::Vector{<:Integer}) where D
```

Extract a `PeriodicGraph{D}` from `g` by removing all edges that have an offset `o` such that `!iszero(o[remove])`.

Contrarily to the [`slice_graph(g::PeriodicGraph{D}, remove::Union{SVector{N},NTuple{N}}) where {D,N}`](@ref) method, the dimensions along which the edges are erased are still kept here.

`remove` is assumed to be sorted and to contain unique elements.

!!! warning
    No verification of the previous assumption will be performed.

