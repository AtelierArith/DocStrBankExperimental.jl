```
structure_constant_table(A::StructureConstantAlgebra; copy::Bool = true) -> Array{_, 3}
```

Given an algebra $A$, return the structure constant table of $A$. See [`structure_constant_algebra`](@ref) for the defining property.

# Examples

```jldoctest
julia> A = associative_algebra(QQ, reshape([1, 0, 0, 2, 0, 1, 1, 0], (2, 2, 2)));

julia> structure_constant_table(A)
2×2×2 Array{QQFieldElem, 3}:
[:, :, 1] =
 1  0
 0  2

[:, :, 2] =
 0  1
 1  0
```
