```
SyzygiesOfRows(A, N)

戻り値: homalg 行列
```

RをAが定義されている環とします。相対行syzygiesの行列SyzygiesOfRows(A, N)は、NをモジュロしたAの左カーネルを生成する行からなる行列です。すなわち、すべての行KがKA+LN=0を満たすR(1×NrRows(A))の自由左モジュールのR-部分モジュールです。ここで、LはR(1×NrRows(N))の行です。

```jldoctest
julia> A = HomalgMatrix(1:9, 3, 3, ZZ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> N = HomalgMatrix(2:10, 3, 3, ZZ)
[2   3    4]
[5   6    7]
[8   9   10]

julia> SyzygiesOfRows(A, N)
[1   0   2]
[0   1   2]
[0   0   3]

julia> SyzygiesOfRows(A,A)
[1   0   0]
[0   1   0]
[0   0   1]
```
