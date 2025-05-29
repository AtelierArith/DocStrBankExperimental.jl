```julia
semilinear_form(
    exprs::AbstractArray,
    vars
) -> Tuple{SparseArrays.SparseMatrixCSC{Symbolics.Num, Int64}, Any}

```

Returns a tuple of a sparse matrix `A`, and a residual vector `c` such that, `A * vars + c` is the same as `exprs`.
