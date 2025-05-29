```
DecideZeroRows(B, A)

戻り値: ホマルグ行列
```

BとAを同じ列数を持ち、同じ環R上で定義された行列とし、SをAの行スパン、すなわちAの行によって張られる自由左モジュールR(1×NrColumns(A))のR-部分モジュールとします。結果はBと同じ形状の行列B′であり、i行目B′^iはBのi行目B^iとSをモジュロした同値である、すなわちB′^i−B^iがAの行スパンSの要素であることを意味します。さらに、行B′^iは、行B^iがSの要素である場合に限りゼロになります。したがって、DecideZeroRowsはBのどの行がAの行に対してゼロであるかを決定します。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> A′ = DecideZeroRows(B, A)
[0   1]
[0   1]
[0   1]

julia> RightDivide(B, A)
"fail"

julia> RightDivide(B - A′, A)
[0   -1   1]
[0   -2   2]
[0   -3   3]

julia> DecideZeroRows(A, A)
[0   0]
[0   0]
[0   0]

julia> C = HomalgMatrix([4, 6, 2, 2], 2, 2, ZZ)
[4   6]
[2   2]

julia> DecideZeroRows(C, A)
[0   0]
[0   0]

julia> DecideZeroRows(A, C)
[1   0]
[1   0]
[1   0]
```
