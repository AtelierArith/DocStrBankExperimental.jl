```
conjugate(a::AssociativeAlgebraElem{_, QuaternionAlgebra})
                             -> AssociativeAlgebraElem{_, QuaternionAlgebra}
```

四元数代数の標準的な反転における $a$ の像を返します。

# 例

```jldoctest
julia> Q = quaternion_algebra(QQ, -1, -1); a = Q([1, 1, 1, 1])
1 + i + j + k

julia> conjugate(a)
1 - i - j - k
```
