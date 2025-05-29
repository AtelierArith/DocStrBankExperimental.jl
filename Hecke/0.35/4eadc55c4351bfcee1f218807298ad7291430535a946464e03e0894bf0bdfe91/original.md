```
is_simple(A::AbstractAssociativeAlgebra) -> Bool
```

Return whether the algebra $A$ is simple.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> is_simple(A)
true
```
