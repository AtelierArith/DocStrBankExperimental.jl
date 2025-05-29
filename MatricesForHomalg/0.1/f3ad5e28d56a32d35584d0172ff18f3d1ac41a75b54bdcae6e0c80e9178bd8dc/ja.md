```
UnionOfColumns(R, nr_rows, list)
```

リスト内の行列を拡張して返します。すべての行列は同じ行数 nr_rows を持ちます。

```jldoctest
julia> UnionOfColumns(ZZ, 2, [])
2 by 0 empty matrix

julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> UnionOfColumns(ZZ, 2, [mat, mat])
[1   2   3   1   2   3]
[4   5   6   4   5   6]
```
