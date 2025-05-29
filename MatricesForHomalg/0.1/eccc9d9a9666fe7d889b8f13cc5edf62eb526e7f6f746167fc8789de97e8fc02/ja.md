```
UnionOfRows(R, nr_cols, list)
```

リスト内の行列をスタックして返します。すべての行列は同じ列数 nr_cols を持っています。

```jldoctest
julia> UnionOfRows(ZZ, 3, [])
0 by 3 の空の行列

julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> UnionOfRows(ZZ, 3, [mat, mat])
[1   2   3]
[4   5   6]
[1   2   3]
[4   5   6]
```
