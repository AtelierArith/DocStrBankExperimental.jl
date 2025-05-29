```
structure_constant_table(A::StructureConstantAlgebra; copy::Bool = true) -> Array{_, 3}
```

与えられた代数 $A$ に対して、$A$ の構造定数テーブルを返します。定義特性については [`structure_constant_algebra`](@ref) を参照してください。

# 例

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
