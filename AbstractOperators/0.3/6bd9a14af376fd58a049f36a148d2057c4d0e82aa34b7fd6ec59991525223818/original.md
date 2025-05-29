`is_linear(A::AbstractOperator)`

Test whether `A` is a `LinearOperator`

```julia
julia> is_linear(Eye(2))
true

julia> is_linear(Sigmoid(Float64,(2,)))
false
```
