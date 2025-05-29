```
dimension_over_center(A::AbstractAssociativeAlgebra) -> Int
```

単純な $K$-代数 $A$ の中心 $C$ を考え、$A$ の $C$-次元を返します。

# 例

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> dimension_of_center(A)
1
```
