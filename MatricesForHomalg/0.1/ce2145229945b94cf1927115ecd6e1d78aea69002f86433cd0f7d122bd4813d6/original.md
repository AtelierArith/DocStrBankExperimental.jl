```
RightDivide(B, A)
```

Returns: a homalg matrix or fail

Let B and A be matrices having the same number of columns and defined over the same ring. The matrix RightDivide(B, A) is a particular solution of the inhomogeneous (one sided) linear system of equations XA=B in case it is solvable. Otherwise fail is returned. The name RightDivide suggests "X=BA^-1".

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

julia> RightDivide(A, B)
[0   3   -2]
[0   2   -1]
[0   1    0]

julia> C = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> RightDivide(A, C)
"fail"

julia> RightDivide(C, A)
"fail"
```
