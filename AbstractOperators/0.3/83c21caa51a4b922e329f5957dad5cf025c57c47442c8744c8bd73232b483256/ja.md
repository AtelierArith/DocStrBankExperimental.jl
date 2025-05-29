`is_orthogonal(A::AbstractOperator)`

`A`が直交しているかどうかをテストします。

```julia
julia> is_orthogonal(DCT(10))
true

julia> is_orthogonal(MatrixOp(randn(3,4)))
false

```
