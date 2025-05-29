`is_full_row_rank(A::AbstractOperator)`

Test whether `A` is easily invertible.

```julia
julia> is_full_column_rank(MatrixOp(randn(4,3)))
true

julia> is_full_column_rank(MatrixOp(randn(3,4)))
false
```
