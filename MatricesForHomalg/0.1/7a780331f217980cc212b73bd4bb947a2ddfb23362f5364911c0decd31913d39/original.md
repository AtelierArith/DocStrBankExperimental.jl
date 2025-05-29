```
UniqueLeftDivide(A, B)
```

Returns: a homalg matrix

Same as SafeLeftDivide, but asserts that the solution is unique.

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> UniqueLeftDivide(B, B)
[1   0]
[0   1]

julia> A = HomalgMatrix([1,2,3,0,5,6,0,0,0], 3, 3, ZZ)
[1   2   3]
[0   5   6]
[0   0   0]

julia> B = HomalgMatrix([1,2,0], 3, 1, ZZ)
[1]
[2]
[0]

julia> UniqueLeftDivide(A, B)
ERROR: The inhomogeneous linear system of equations AX=B has no unique solution
```
