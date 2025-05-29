```
SortedPeriodicGraphEmbedding{T}(graph::PeriodicGraph{D}, placement::AbstractMatrix, cell::Cell=Cell()) where {D,T}
```

Build a [`PeriodicGraphEmbedding{D,T}`](@ref) from the corresponding `graph` and `placement` of the vertices, so that the result has its vertices sorted by position.

Return the [`PeriodicGraphEmbedding`](@ref) as well as the permutation of the columns of `placement` that yielded the resulting order on the vertices.

The `cell` optional argument will not be used if `D > 3`.

!!! warning
    This function modifies the input `graph` if any element of `placement` is out of [0, 1).


See also [`PeriodicGraphEmbedding{D,T}(graph, placement::AbstractMatrix{T}, cell) where {D,T}`](@ref) and [`SortedPeriodicGraphEmbedding(graph, placement::AbstractMatrix, cell)`](@ref).
