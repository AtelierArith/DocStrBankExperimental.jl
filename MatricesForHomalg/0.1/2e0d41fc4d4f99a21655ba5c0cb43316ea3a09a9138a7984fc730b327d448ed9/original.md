```
HomalgMatrix(L, r, c, R)
```

Construct a (r x c)-matrix over the ring R with L as list of entries

```jldoctest
julia> mat1 = HomalgMatrix([1,2,3,4,5,6], 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> mat2 = HomalgMatrix([[1,2,3],[4,5,6]], 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> mat1 == mat2
true
```
