```
dimension_of_center(A::AbstractAssociativeAlgebra) -> Int
```

与えられた $K$-代数に対して、$A$ の中心の $K$-次元を返します。

# 例

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> dimension_of_center(A)
1
```
