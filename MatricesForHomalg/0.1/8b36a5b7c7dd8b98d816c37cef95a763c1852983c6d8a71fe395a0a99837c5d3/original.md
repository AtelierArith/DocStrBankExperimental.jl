```
SafeLeftDivide(A, B, L)
```

Returns: a homalg matrix

Same as LeftDivide, but asserts that the result is not fail.

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> L = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> B = HomalgMatrix([5, 5, 11, 9, 17, 13], 3, 2, ZZ)
[ 5    5]
[11    9]
[17   13]

julia> SafeLeftDivide(A, B, L)
[0   0]
[0   0]

julia> B = HomalgMatrix([3, 5, 0, 9, 11, 13], 3, 2, ZZ)
[ 3    5]
[ 0    9]
[11   13]

julia> SafeLeftDivide(A, B, L)
ERROR: Unable to solve linear system
```
