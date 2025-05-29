```
is_commutative(A::AbstractAssociativeAlgebra) -> Bool
```

Return whether $A$ is commutative.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> is_commutative(A)
false
```
