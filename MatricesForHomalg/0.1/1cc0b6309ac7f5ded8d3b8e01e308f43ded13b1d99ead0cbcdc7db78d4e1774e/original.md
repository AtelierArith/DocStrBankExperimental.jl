```
ConvertMatrixToRow(mat)
```

Unfold the matrix M row-wise into a row.

```jldoctest
julia> mat = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> ConvertMatrixToRow(mat)
[2   3   4   5   6   7]

```
