`is_invertible(A::AbstractOperator)`

`A`が簡単に逆行列を持つかどうかをテストします。

```julia
julia> is_invertible(DFT(10))
true

julia> is_invertible(MatrixOp(randn(3,4)))
false

```
