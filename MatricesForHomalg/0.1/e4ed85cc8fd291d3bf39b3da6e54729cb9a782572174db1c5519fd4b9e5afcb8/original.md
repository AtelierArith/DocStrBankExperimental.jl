```
UniqueRightDivide(B, A)
```

Returns: a homalg matrix

Same as SafeRightDivide, but asserts that the solution is unique.

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(3:8, 3, 2, ZZ)
[3   4]
[5   6]
[7   8]

julia> RightDivide(B, A)
[0    1   0]
[0    0   1]
[0   -1   2]

julia> UniqueRightDivide(B, A)
ERROR: The inhomogeneous linear system of equations XA=B has no unique solution

julia> mat = HomalgIdentityMatrix(3, ZZ)
[1   0   0]
[0   1   0]
[0   0   1]

julia> UniqueRightDivide(mat, mat)
[1   0   0]
[0   1   0]
[0   0   1]
```
