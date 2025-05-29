```
UnionOfRows(R, nr_cols, list)
```

Return the matrices in list stacked, where all of them have same number of columns nr_cols.

```jldoctest
julia> UnionOfRows(ZZ, 3, [])
0 by 3 empty matrix

julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> UnionOfRows(ZZ, 3, [mat, mat])
[1   2   3]
[4   5   6]
[1   2   3]
[4   5   6]
```
