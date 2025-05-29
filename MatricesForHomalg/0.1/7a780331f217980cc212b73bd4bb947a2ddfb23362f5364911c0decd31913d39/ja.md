```
UniqueLeftDivide(A, B)
```

返す: homalg 行列

SafeLeftDivide と同じですが、解が一意であることを主張します。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> UniqueLeftDivide(B, B)
[1   0]
[0   1]

julia> A = HomalgMatrix([1,2,3,0,5,6,0,0,0], 3, 3, ZZ)
[1   2   3]
[0   5   6]
[0   0   0]

julia> B = HomalgMatrix([1,2,0], 3, 1, ZZ)
[1]
[2]
[0]

julia> UniqueLeftDivide(A, B)
ERROR: 非同次線形方程式 AX=B は一意の解を持ちません
```
