```
HomalgDiagonalMatrix(L, R)
```

Construct a diagonal matrix over the ring R using the list L of diagonal entries

```jldoctest
julia> mat = HomalgDiagonalMatrix(1:5, ZZ)
[1   0   0   0   0]
[0   2   0   0   0]
[0   0   3   0   0]
[0   0   0   4   0]
[0   0   0   0   5]
```
