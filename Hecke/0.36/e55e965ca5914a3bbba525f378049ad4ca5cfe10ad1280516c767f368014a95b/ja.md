```
structure_constant_algebra(K::SimpleNumField) -> StructureConstantAlgebra, Map
```

数体 $L/K$ が与えられたとき、$L$ を $K$-代数 $A$ として返し、$A \to L$ の $K$-線形写像を返します。

# 例

```jldoctest
julia> L, = quadratic_field(2);

julia> structure_constant_algebra(L)
(Structure constant algebra of dimension 2 over QQ, Map: structure constant algebra -> L)
```
