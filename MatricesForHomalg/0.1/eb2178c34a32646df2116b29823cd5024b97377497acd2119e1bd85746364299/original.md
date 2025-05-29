```
LeftDivide(A, B, L)
```

Returns: a homalg matrix or fail

Let A, B and L be matrices having the same number of columns and defined over the same ring. The matrix LeftDivide( A, B, L ) is a particular solution of the inhomogeneous (one sided) linear system of equations AX+LY=B in case it is solvable (for some Y which is forgotten). Otherwise fail is returned. The name LeftDivide suggests "X=A−1B modulo L"

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

julia> LeftDivide(A, B, L)
[0   0]
[0   0]

julia> B = HomalgMatrix([3, 5, 0, 9, 11, 13], 3, 2, ZZ)
[ 3    5]
[ 0    9]
[11   13]

julia> LeftDivide(A, B, L)
"fail"
```
