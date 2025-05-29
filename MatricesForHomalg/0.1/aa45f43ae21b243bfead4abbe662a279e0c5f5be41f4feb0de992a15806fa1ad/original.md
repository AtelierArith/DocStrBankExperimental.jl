```
CertainColumns(mat, list)
```

Return the matrix of which the i-th column is the k-th column of the homalg matrix M, where k=list[i].

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
