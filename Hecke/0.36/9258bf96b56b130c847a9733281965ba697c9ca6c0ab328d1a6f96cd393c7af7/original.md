```
conjugate(a::AssociativeAlgebraElem{_, QuaternionAlgebra})
                             -> AssociativeAlgebraElem{_, QuaternionAlgebra}
```

Return the image of $a$ under the canonical involution of the quaternion algebra.

# Examples

```jldoctest
julia> Q = quaternion_algebra(QQ, -1, -1); a = Q([1, 1, 1, 1])
1 + i + j + k

julia> conjugate(a)
1 - i - j - k
```
