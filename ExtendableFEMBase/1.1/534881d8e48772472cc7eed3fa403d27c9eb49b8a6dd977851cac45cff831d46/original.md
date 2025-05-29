```julia
submatrix(
    A::ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti},
    srows,
    scols;
    factor
) -> ExtendableSparse.ExtendableSparseMatrixCSC

```

Generates an ExtendableSparseMatrix from the submatrix for the given row and col numbers
