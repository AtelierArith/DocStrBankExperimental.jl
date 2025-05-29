```
is_commutative(A::AbstractAssociativeAlgebra) -> Bool
```

$$
A
$$

が可換であるかどうかを返します。

# 例

```jldoctest
julia> A = matrix_algebra(QQ, 2);

julia> is_commutative(A)
false
```
