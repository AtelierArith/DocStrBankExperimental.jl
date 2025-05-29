```
RightDivide(B, A)
```

返り値: homalg 行列または失敗

B と A を同じ列数を持ち、同じ環上で定義された行列とします。行列 RightDivide(B, A) は、解が存在する場合において、非同次（片側）線形方程式系 XA=B の特定の解です。そうでない場合は失敗が返されます。RightDivide という名前は「X=BA^-1」を示唆しています。

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

julia> RightDivide(A, B)
[0   3   -2]
[0   2   -1]
[0   1    0]

julia> C = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> RightDivide(A, C)
"fail"

julia> RightDivide(C, A)
"fail"
```
