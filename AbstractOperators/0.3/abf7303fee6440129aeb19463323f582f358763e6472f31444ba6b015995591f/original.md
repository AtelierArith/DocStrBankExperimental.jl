`is_AAc_diagonal(A::AbstractOperator)`

Test whether `A*A'` is diagonal.

```julia
julia> is_AAc_diagonal(Eye(10))
true

julia> is_AAc_diagonal(GetIndex((10,),1:3))
false

```
