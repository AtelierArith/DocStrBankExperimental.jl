```
is_simple(A::AbstractAssociativeAlgebra) -> Bool
```

代数 $A$ が単純であるかどうかを返します。

# 例

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> is_simple(A)
true
```
