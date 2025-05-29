```
structure_constant_algebra(K::SimpleNumField) -> StructureConstantAlgebra, Map
```

数体 $L/K$ が与えられたとき、$K$-代数 $A$ と $A \to L$ の $K$-線形写像を共に返します。

# 例

```jldoctest
julia> L, = quadratic_field(2);

julia> structure_constant_algebra(L)
(Structure constant algebra of dimension 2 over QQ, Map: structure constant algebra -> L)
```
