```
zero_algebra([T, ] K::Field) -> AbstractAssociativeAlgebra
```

Return the zero ring as an algebra over the field $K$.

The optional first argument determines the type of the algebra, and can be `StructureConstantAlgebra` (default) or `MatrixAlgebra`.

# Examples

```jldoctest
julia> A = zero_algebra(QQ)
Structure constant algebra of dimension 0 over QQ
```
