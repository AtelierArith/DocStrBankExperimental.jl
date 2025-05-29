```
SyzygiesOfRows(A)
```

ホマルグ行列を返します。RをAが定義されている環とします（R:= HomalgRing(A)）。行のシジーの行列SyzygiesGeneratorsOfRows(A)は、Aの左カーネルを生成する行からなる行列です。すなわち、すべての行XがXA=0を満たす自由左モジュールR(1xNrRows(A))のR-部分モジュールです。

```jldoctest
julia> A = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> S = SyzygiesOfRows(A)
[1   -2   1]

julia> S*A
[0   0]
```
