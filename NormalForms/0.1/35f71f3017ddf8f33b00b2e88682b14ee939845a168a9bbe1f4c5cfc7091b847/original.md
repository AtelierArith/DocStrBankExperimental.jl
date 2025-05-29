```
hnfc!(M::AbstractMatrix{<:Integer}, R::RoundingMode = NegativeOffDiagonal)
    -> ColumnHermite{eltype(M),typeof(M)}
```

Calculates the column Hermite normal form of the integer matrix `M` in-place, returning a `ColumnHermite` describing the elements of the factorization.
