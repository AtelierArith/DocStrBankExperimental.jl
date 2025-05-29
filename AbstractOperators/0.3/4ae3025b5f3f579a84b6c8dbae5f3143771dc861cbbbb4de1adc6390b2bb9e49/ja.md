`is_eye(A::AbstractOperator)`

`A`が単位演算子であるかどうかをテストします

```julia
julia> is_eye(Eye(10))
true

julia> is_eye(Zeros(Float64,(10,),(10,)))
false

```
