```
dimension_over_center(A::AbstractAssociativeAlgebra) -> Int
```

Given a simple $K$-algebra with center $C$, return the $C$-dimension $A$.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> dimension_of_center(A)
1
```
