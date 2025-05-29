```
IsZero(mat)
```

Return true if mat is a zero matrix, otherwise false

```jldoctest
julia> mat = HomalgZeroMatrix(3, 2, ZZ)
[0   0]
[0   0]
[0   0]

julia> IsZero(mat)
true
```
