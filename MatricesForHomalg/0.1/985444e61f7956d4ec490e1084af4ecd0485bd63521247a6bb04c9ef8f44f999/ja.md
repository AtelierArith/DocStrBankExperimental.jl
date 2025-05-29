```
RightDivide(B, A, L)
```

返り値: homalg 行列または失敗

B、A、およびLを同じ列数を持ち、同じ環上で定義された行列とします。行列 RightDivide( B, A, L ) は、解が存在する場合（忘れられたYのために）における非同次（片側の）線形方程式系 XA+YL=B の特定の解です。そうでない場合は失敗が返されます。RightDivideという名前は「X=BA−1 modulo L」を示唆しています。

```jldoctest
julia> A = HomalgMatrix(1:9, 3, 3, ZZ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> B = HomalgMatrix([3, 5, 7, 13, 16, 19, 29, 33, 37], 3, 3, ZZ)
[ 3    5    7]
[13   16   19]
[29   33   37]

julia> L = HomalgMatrix(2:10, 3, 3, ZZ)
[2   3    4]
[5   6    7]
[8   9   10]

julia> X = RightDivide(B, A, L)
[0   0   -2]
[0   0   -1]
[0   0    0]

julia> B = HomalgMatrix([3, 5, 7, 0, 16, 19, 0, 33, 37], 3, 3, ZZ)
[3    5    7]
[0   16   19]
[0   33   37]

julia> RightDivide(B, A, L)
"fail"
```
