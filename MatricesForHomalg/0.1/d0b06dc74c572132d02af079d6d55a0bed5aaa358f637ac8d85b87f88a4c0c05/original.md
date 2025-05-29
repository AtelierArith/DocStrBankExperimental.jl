```
ColumnRankOfMatrix(mat)
```

Returns the column rank of the matrix mat as a nonnegative integer.

```jldoctest
julia> mat1 = TransposedMatrix(HomalgMatrix(4:9, 3, 2, ZZ))
[4   6   8]
[5   7   9]

julia> ColumnRankOfMatrix(mat1)
2

julia> mat2 = HomalgIdentityMatrix(3, ZZ)
[1   0   0]
[0   1   0]
[0   0   1]

julia> ColumnRankOfMatrix(mat2)
3
```
