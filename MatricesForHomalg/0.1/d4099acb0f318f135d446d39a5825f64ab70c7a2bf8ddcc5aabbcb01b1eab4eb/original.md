```
SafeLeftDivide(A, B)
```

Returns: a homalg matrix

Same as LeftDivide, but asserts that the result is not fail.

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> C = HomalgMatrix([1,0,0,0,0,0], 3, 2, ZZ)
[1   0]
[0   0]
[0   0]

julia> SafeLeftDivide(B, B)
[1   0]
[0   1]

julia> SafeLeftDivide(A, B)
[0   -1]
[1    2]

julia> SafeLeftDivide(C, B)
ERROR: Unable to solve linear system
```
