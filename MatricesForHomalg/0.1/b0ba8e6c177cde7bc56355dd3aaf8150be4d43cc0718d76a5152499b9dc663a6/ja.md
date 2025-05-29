```
SyzygiesOfColumns(A, N)

戻り値: homalg 行列
```

RをMが定義されている環とします。相対列シジーの行列SyzygiesOfColumns(A,N)は、Aの右カーネルの列をNで割ったものであり、すなわち、すべての列KがAK+NL=0を満たすR(NrColumns(N)×1)の列L∈R(NrColumns(N)×1に対して、自由右モジュールR(NrColumns(A)×1)のR-部分モジュールを構成します。

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> N = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> SyzygiesOfColumns(A, N)
[1   0]
[0   1]
```
