```julia
semiquadratic_form(
    exprs,
    vars
) -> Tuple{SparseArrays.SparseMatrixCSC{Symbolics.Num, Int64}, SparseArrays.SparseMatrixCSC{Symbolics.Num, Int64}, Any, Any}

```

Returns a tuple of 4 objects:

1. a matrix `A` of dimensions (m x n)
2. a matrix `B` of dimensions (m x (n+1)*n/2)
3. a vector `v2` of length (n+1)*n/2 containing monomials of `vars` upto degree 2 and zero where they are not required.
4. a residual vector `c` of length m.

where `n == length(exprs)` and `m == length(vars)`.

The result is arranged such that, `A * vars + B * v2 + c` is the same as `exprs`.
