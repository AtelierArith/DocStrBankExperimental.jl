```
central_primitive_idempotents(A::AbstractAssociativeAlgebra) -> Vector
```

Returns the central primitive idempotents of `A`.

```jldoctest
julia> G = small_group(5, 1);

julia> QG = QQ[G];

julia> length(central_primitive_idempotents(QG))
2
```
