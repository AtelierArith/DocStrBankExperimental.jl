```
SafeRightDivide(B, A)
```

返り値: homalg 行列

RightDivide と同じですが、結果が失敗しないことを確認します。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(3:8, 3, 2, ZZ)
[3   4]
[5   6]
[7   8]

julia> SafeRightDivide(B, A)
[0    1   0]
[0    0   1]
[0   -1   2]

julia> SafeRightDivide(A, B)
[0   3   -2]
[0   2   -1]
[0   1    0]

julia> SafeRightDivide(B, B)
[0   2   -1]
[0   1    0]
[0   0    1]

julia> B = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> SafeRightDivide(A, B)
ERROR: 線形システムを解決できません
```
