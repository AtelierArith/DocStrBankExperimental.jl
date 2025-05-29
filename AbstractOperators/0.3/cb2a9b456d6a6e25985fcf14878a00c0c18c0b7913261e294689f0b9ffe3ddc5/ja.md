`is_null(A::AbstractOperator)`

`A`がnullであるかどうかをテストします。

```julia
julia> is_null(Zeros(Float64,(10,),(10,)))
true

julia> is_null(Eye(10))
false

```
