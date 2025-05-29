```
SortedPeriodicGraphEmbedding(graph::PeriodicGraph{D}, placement::AbstractMatrix, cell::Cell=Cell()) where D
```

Build a [`PeriodicGraphEmbedding{D,T}`](@ref) from the corresponding `graph` and `placement` of the vertices, so that the result has its vertices sorted by position. `T` is determined as the smallest type between `Rational{Int32}`, `Rational{Int64}`, `Rational{Int128}` and `Rational{BigInt}` that can fit all the elements of `placement` with some additional margin.

Return the [`PeriodicGraphEmbedding`](@ref) as well as the permutation of the columns of `placement` that yielded the resulting order on the vertices.

The `cell` optional argument will not be used if `D > 3`.

!!! warning
    This function modifies the input `graph` if any element of `placement` is out of [0, 1).


!!! tip
    This function is inherently type-unstable since `T` cannot be statically determined. This can be useful because having a too large `T` may slow down later computations.

    To provide the parameter explicitly, pass it to the `SortedPeriodicGraphEmbedding` constructor by calling `SortedPeriodicGraphEmbedding{T}(graph, placement, cell)`.


See also [`PeriodicGraphEmbedding{D,T}(graph, placement::AbstractMatrix{T}, cell) where {D,T}`](@ref).
