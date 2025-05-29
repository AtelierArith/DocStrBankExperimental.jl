```
DecideZeroColumns(B, A)

戻り値: homalg 行列
```

B と A を同じ行数を持ち、同じ環 R 上で定義された行列とし、S を A の列スパン、すなわち A の列によって張られる自由右モジュール R(NrRows(A)×1) の R-部分モジュールとします。結果は B と同じ形状を持つ行列 B′ であり、i 番目の列 B′*i は B の i 番目の列 B*i と S に関して同値である、すなわち B′*i−B*i は A の列スパン S の要素です。さらに、列 B′*i は、列 B*i が S の要素である場合に限りゼロになります。したがって、DecideZeroColumns は B のどの列が A の列に関してゼロであるかを決定します。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix([3, 1, 7, 1, 11, 1], 3, 2, ZZ)
[ 3   1]
[ 7   1]
[11   1]

julia> DecideZeroColumns(B, A)
[0   0]
[0   0]
[0   0]
```
