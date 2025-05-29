```
CertainRows(mat, list)
```

i 番目の行がホマルグ行列 M の k 番目の行である行列を返します。ここで、k=list[i] です。

```jldoctest
julia> mat = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> CertainRows(mat, [2, 2, 1])
[4   5]
[4   5]
[2   3]

julia> CertainRows(mat, [])
0 by 2 empty matrix

julia> CertainRows(mat, 4:3)
0 by 2 empty matrix
```
