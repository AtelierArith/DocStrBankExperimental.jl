```
LeftDivide(A, B)
```

返り値: homalg 行列または失敗

行列 A と B が同じ行数を持ち、同じ環上で定義されているとします。行列 LeftDivide(A, B) は、解が存在する場合において、非同次（片側）線形方程式系 AX=B の特定の解です。そうでない場合は失敗が返されます。LeftDivide という名前は「X=A^{-1}B」を示唆しています。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> C = HomalgMatrix([1,0,0,0,0,0], 3, 2, ZZ)
[1   0]
[0   0]
[0   0]

julia> LeftDivide(B, B)
[1   0]
[0   1]

julia> LeftDivide(A, B)
[0   -1]
[1    2]

julia> LeftDivide(C, B)
"fail"
```
