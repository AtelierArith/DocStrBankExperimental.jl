```
IsSymmetricMatrix(mat)
```

Return true if the matrix mat is symmetric with respect to its main diagonal, otherwise false

```jldoctest
julia> mat = HomalgMatrix([1,2,3,2,4,5,3,5,6], 3, 3, ZZ)
[1   2   3]
[2   4   5]
[3   5   6]

julia> IsSymmetricMatrix(mat)
true
```
