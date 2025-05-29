```
LeftDivide(A, B, L)
```

返り値: homalg 行列または失敗

行列 A, B および L は同じ列数を持ち、同じ環上で定義されているとします。行列 LeftDivide( A, B, L ) は、解が存在する場合（忘れられた Y のための）における非同次（片側）線形方程式系 AX+LY=B の特定の解です。そうでない場合は失敗が返されます。LeftDivide という名前は「X=A−1B modulo L」を示唆しています。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> L = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> B = HomalgMatrix([5, 5, 11, 9, 17, 13], 3, 2, ZZ)
[ 5    5]
[11    9]
[17   13]

julia> LeftDivide(A, B, L)
[0   0]
[0   0]

julia> B = HomalgMatrix([3, 5, 0, 9, 11, 13], 3, 2, ZZ)
[ 3    5]
[ 0    9]
[11   13]

julia> LeftDivide(A, B, L)
"fail"
```
