```
ConvertMatrixToColumn(mat)
```

Unfold the matrix M column-wise into a column.

```jldoctest
julia> mat = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> ConvertMatrixToColumn(mat)
[2]
[4]
[6]
[3]
[5]
[7]

```
