```
SyzygiesOfColumns(A)
```

ホマルグ行列を返します。RをAが定義されている環とします（R:=HomalgRing(A)）。列のシジーの行列SyzygiesGeneratorsOfColumns(A)は、Aの右カーネルを生成する列を持つ行列です。すなわち、AX=0を満たすすべての列Xからなる自由右モジュールR(NrColumns(A)x1)のR-部分モジュールです。

```jldoctest
julia> A = TransposedMatrix(HomalgMatrix(4:9, 3, 2, ZZ))
[4   6   8]
[5   7   9]

julia> S = SyzygiesOfColumns(A)
[ 1]
[-2]
[ 1]

julia> A*S
[0]
[0]
```
