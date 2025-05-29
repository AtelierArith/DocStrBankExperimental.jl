```
LeftDivide(A, B)
```

Returns: a homalg matrix or fail

Let A and B be matrices having the same number of rows and defined over the same ring. The matrix LeftDivide(A, B) is a particular solution of the inhomogeneous (one sided) linear system of equations AX=B in case it is solvable. Otherwise fail is returned. The name LeftDivide suggests "X=A^{-1}B".

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

julia> LeftDivide(B, B)
[1   0]
[0   1]

julia> LeftDivide(A, B)
[0   -1]
[1    2]

julia> LeftDivide(C, B)
"fail"
```
