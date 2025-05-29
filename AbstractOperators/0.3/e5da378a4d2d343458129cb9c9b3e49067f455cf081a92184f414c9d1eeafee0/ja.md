`is_full_row_rank(A::AbstractOperator)`

`A`が簡単に逆転可能かどうかをテストします。

```julia
julia> is_full_row_rank(MatrixOp(randn(3,4)))
true

julia> is_full_row_rank(MatrixOp(randn(4,3)))
false
```
