`is_AAc_diagonal(A::AbstractOperator)`

`A*A'`が対角行列であるかどうかをテストします。

```julia
julia> is_AAc_diagonal(Eye(10))
true

julia> is_AAc_diagonal(GetIndex((10,),1:3))
false

```
