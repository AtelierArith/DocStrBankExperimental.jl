```
structure_constant_algebra(K::SimpleNumField) -> StructureConstantAlgebra, Map
```

Given a number field $L/K$, return $L$ as a $K$-algebra $A$ together with a $K$-linear map $A \to L$.

# Examples

```jldoctest
julia> L, = quadratic_field(2);

julia> structure_constant_algebra(L)
(Structure constant algebra of dimension 2 over QQ, Map: structure constant algebra -> L)
```
