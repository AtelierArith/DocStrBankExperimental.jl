`is_AcA_diagonal(A::AbstractOperator)`

Test whether `A'*A` is diagonal.

```julia
julia> is_AcA_diagonal(Eye(10))
true

julia> is_AcA_diagonal(GetIndex((10,),1:3))
false

```
