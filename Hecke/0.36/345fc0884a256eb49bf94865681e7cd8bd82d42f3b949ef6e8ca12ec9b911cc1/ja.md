```
is_split_with_zero_divisor(A::QuaternionAlgebra) -> Bool, AssociativeAlgebraElem
```

与えられた四元数代数 $A$ に対して、$A$ が分割されているかどうかを返し、$A$ が分割されている場合はゼロ除数である要素を返します。

# 例

```jldoctest
julia> A = quaternion_algebra(QQ, 1, 4);

julia> is_split_with_zero_divisor(A)
(true, 1 + i)

julia> A = quaternion_algebra(QQ, -1, -1);

julia> is_split_with_zero_divisor(A)
(false, 0)
```
