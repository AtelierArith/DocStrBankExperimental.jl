```
rational_solve(::Val{N}, A::SparseMatrixCSC{Int,Int}, Y::Matrix{Int}) where N
```

Fallback solver for [`dixon_solve`](@ref) which performs an LU decomposition followed by forward and backward substitutions. Return an empty matrix if `A` is not invertible.

In general, it is slower than [`dixon_solve`](@ref).

!!! warning
    `A` must be square and `N` must be equal to `size(Y)[2]` or the function may fail, error, or cause a silent corruption without notice.

