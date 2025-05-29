```
TransposedMatrix(mat)
```

Return the transposed matrix of mat

```jldoctest
julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> TransposedMatrix(mat)
[1   4]
[2   5]
[3   6]
```
