`is_eye(A::AbstractOperator)`

Test whether `A` is an Identity operator

```julia
julia> is_eye(Eye(10))
true

julia> is_eye(Zeros(Float64,(10,),(10,)))
false

```
