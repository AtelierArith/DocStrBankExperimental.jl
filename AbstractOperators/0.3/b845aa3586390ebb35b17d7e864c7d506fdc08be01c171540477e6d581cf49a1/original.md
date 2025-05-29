`is_diagonal(A::AbstractOperator)`

Test whether `A` is diagonal.

```julia
julia> is_diagonal(Eye(10))
true

julia> is_diagonal(FiniteDiff((10,)))
false

```
