```
UnionOfColumns(R, nr_rows, list)
```

Return the matrices in list augmented, where all of them have same number of rows nr_rows. .

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
