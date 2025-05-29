```
UniqueRightDivide(B, A)
```

返す: homalg 行列

SafeRightDivide と同じですが、解が一意であることを主張します。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(3:8, 3, 2, ZZ)
[3   4]
[5   6]
[7   8]

julia> RightDivide(B, A)
[0    1   0]
[0    0   1]
[0   -1   2]

julia> UniqueRightDivide(B, A)
ERROR: 非同次線形方程式 XA=B は一意の解を持ちません

julia> mat = HomalgIdentityMatrix(3, ZZ)
[1   0   0]
[0   1   0]
[0   0   1]

julia> UniqueRightDivide(mat, mat)
[1   0   0]
[0   1   0]
[0   0   1]
```
