```
BasisOfRows(mat)
```

Return the triangular form of mat

```jldoctest
julia> mat = HomalgMatrix(1:9, 3, 3, ZZ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> BasisOfRows(mat)
[1   2   3]
[0   3   6]

julia> mat = HomalgMatrix(1:9, 3, 3, QQ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> BasisOfRows(mat)
[1   0   -1]
[0   1    2]
```
