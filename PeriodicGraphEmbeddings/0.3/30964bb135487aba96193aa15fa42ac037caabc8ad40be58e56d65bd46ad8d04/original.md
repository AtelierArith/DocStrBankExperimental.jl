```
PeriodicGraphEmbedding{D,T}(graph::PeriodicGraph{D}, placement::AbstractMatrix{T}, cell::Cell=Cell()) where {D,T}
PeriodicGraphEmbedding{D}(graph::PeriodicGraph{D}, placement::AbstractMatrix{T}, cell::Cell=Cell()) where D
PeriodicGraphEmbedding(graph::PeriodicGraph{D}, placement::AbstractMatrix{T}, cell::Cell=Cell())
```

Build a [`PeriodicGraphEmbedding{D,T}`](@ref) from the corresponding `graph` and `placement` of the vertices, such that each vertex has its fractional coordinate represented in a column of the matrix.

Coordinates out of [0, 1) are translated back to the unit cell with the corresponding offset added to the graph.

The `cell` optional argument will not be used if `D > 3`.

!!! warning
    This function modifies the input `graph` if any element of `placement` is out of [0, 1).


!!! note
    To obtain a [`PeriodicGraphEmbedding`](@ref) with sorted positions, use [`SortedPeriodicGraphEmbedding`](@ref) instead

