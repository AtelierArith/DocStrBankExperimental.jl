```
dixon_solve(::Val{N}, A::SparseMatrixCSC{Int,Int}, Y::Matrix{Int}) where N
```

Specialized solver for the linear system `A*X = Y` where `A` is a sparse integer `n×n` matrix and `Y` is a dense integer `n×N` matrix, using Dixon's method.

Return `X` as either a `Matrix{Rational{Int64}}`, a `Matrix{Rational{Int128}}` or a `Matrix{Rational{BigInt}}`, whichever smallest type can hold all its values.

Return an empty matrix if `A` is not invertible.

!!! warning
    `A` must be square and `N` must be equal to `size(Y)[2]` or the function may fail, error, or cause a silent corruption without notice.

