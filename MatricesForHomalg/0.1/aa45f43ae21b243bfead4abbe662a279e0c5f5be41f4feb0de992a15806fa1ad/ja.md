```
CertainColumns(mat, list)
```

i 番目の列が homalg 行列 M の k 番目の列である行列を返します。ここで、k=list[i] です。

```jldoctest
julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> CertainColumns(mat, [2, 2, 1])
[2   2   1]
[5   5   4]

julia> CertainColumns(mat, [])
2 by 0 empty matrix

julia> CertainColumns(mat, 4:3)
2 by 0 empty matrix
```
