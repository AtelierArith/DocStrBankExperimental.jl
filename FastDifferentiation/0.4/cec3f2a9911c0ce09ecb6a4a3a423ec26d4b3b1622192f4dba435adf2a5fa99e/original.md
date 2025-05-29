```
make_Expr(
    A::SparseMatrixCSC{<:Node,<:Integer},
    input_variables::AbstractVector{<:Node},
    in_place::Bool, init_with_zeros::Bool
)
```

`init_with_zeros` argument is not used for sparse matrices.
