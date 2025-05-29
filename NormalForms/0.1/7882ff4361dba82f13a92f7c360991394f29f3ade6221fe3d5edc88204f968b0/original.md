```
hnfc(M::AbstractMatrix{T<:Integer}) -> ColumnHermite{T,typeof(M)}
    -> ColumnHermite{eltype(M),typeof(M)}
```

Calculates the column Hermite normal form of the integer matrix `M` in-place, returning a `ColumnHermite` describing the elements of the factorization. Unlike `hnfc!()`, this function creates a copy of the input matrix rather than modifying it in-place.
