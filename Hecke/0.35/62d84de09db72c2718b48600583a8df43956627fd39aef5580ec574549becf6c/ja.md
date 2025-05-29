```
central_primitive_idempotents(A::AbstractAssociativeAlgebra) -> Vector
```

`A`の中心的な原始冪等元を返します。

```jldoctest
julia> G = small_group(5, 1);

julia> QG = QQ[G];

julia> length(central_primitive_idempotents(QG))
2
```
