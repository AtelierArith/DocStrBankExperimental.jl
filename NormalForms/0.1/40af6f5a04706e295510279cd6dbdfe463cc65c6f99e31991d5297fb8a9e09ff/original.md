```
hnfr(M::AbstractMatrix{<:Integer}, R::RoundingMode = NegativeOffDiagonal)
    -> RowHermite{eltype(M),typeof(M)}
```

Calculates the row Hermite normal form of the integer matrix `M` in-place, returning a `RowHermite` describing the elements of the factorization. Unlike `hnfr!()`, this function creates a copy of the input matrix rather than modifying it in-place.
