`is_diagonal(A::AbstractOperator)`

`A`が対角行列であるかどうかをテストします。

```julia
julia> is_diagonal(Eye(10))
true

julia> is_diagonal(FiniteDiff((10,)))
false

```
