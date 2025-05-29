```
dimension_of_center(A::AbstractAssociativeAlgebra) -> Int
```

Given a $K$-algebra, return the $K$-dimension of the center of $A$.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> dimension_of_center(A)
1
```
