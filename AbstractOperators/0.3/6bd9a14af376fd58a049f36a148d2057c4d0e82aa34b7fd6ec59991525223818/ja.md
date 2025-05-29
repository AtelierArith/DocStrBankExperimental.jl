`is_linear(A::AbstractOperator)`

`A`が`LinearOperator`であるかどうかをテストします。

```julia
julia> is_linear(Eye(2))
true

julia> is_linear(Sigmoid(Float64,(2,)))
false
```
