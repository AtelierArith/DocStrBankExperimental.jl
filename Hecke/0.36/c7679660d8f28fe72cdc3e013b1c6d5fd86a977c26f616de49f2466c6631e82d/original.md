```
center(A::AbstractAssociativeAlgebra)
                                   -> StructureConstantAlgebra, Map
```

Returns the center $C$ of $A$ and the inclusion $C \to A$. Note that $C$ itself is an algebra.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> C, CtoA = center(A);

julia> C
Structure constant algebra of dimension 1 over QQ
```
