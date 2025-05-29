```
ZeroRows(mat)
```

Return a (possibly empty) list of positive integers. The list of zero rows of the matrix A.

```jldoctest
julia> mat = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> ZeroRows(mat)
Int64[]

julia> mat = HomalgMatrix([0, 2, 6, 0, 0, 0], 3, 2, ZZ)
[0   2]
[6   0]
[0   0]

julia> ZeroRows(mat)
1-element Vector{Int64}:
 3

julia> mat = HomalgZeroMatrix(3,3,ZZ)
[0   0   0]
[0   0   0]
[0   0   0]

julia> ZeroRows(mat)
3-element Vector{Int64}:
 1
 2
 3
```
