```
is_split_with_zero_divisor(A::QuaternionAlgebra) -> Bool, AssociativeAlgebraElem
```

Given a quaternion algebra $A$, return whether $A$ is split together with an element, which is a zero-divisor in case $A$ is split.

# Examples

```jldoctest
julia> A = quaternion_algebra(QQ, 1, 4);

julia> is_split_with_zero_divisor(A)
(true, 1 + i)

julia> A = quaternion_algebra(QQ, -1, -1);

julia> is_split_with_zero_divisor(A)
(false, 0)
```
