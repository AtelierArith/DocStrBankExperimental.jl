```
RightDivide(B, A, L)
```

Returns: a homalg matrix or fail

Let B, A and L be matrices having the same number of columns and defined over the same ring. The matrix RightDivide( B, A, L ) is a particular solution of the inhomogeneous (one sided) linear system of equations XA+YL=B in case it is solvable (for some Y which is forgotten). Otherwise fail is returned. The name RightDivide suggests "X=BA−1 modulo L".

```jldoctest
julia> A = HomalgMatrix(1:9, 3, 3, ZZ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> B = HomalgMatrix([3, 5, 7, 13, 16, 19, 29, 33, 37], 3, 3, ZZ)
[ 3    5    7]
[13   16   19]
[29   33   37]

julia> L = HomalgMatrix(2:10, 3, 3, ZZ)
[2   3    4]
[5   6    7]
[8   9   10]

julia> X = RightDivide(B, A, L)
[0   0   -2]
[0   0   -1]
[0   0    0]

julia> B = HomalgMatrix([3, 5, 7, 0, 16, 19, 0, 33, 37], 3, 3, ZZ)
[3    5    7]
[0   16   19]
[0   33   37]

julia> RightDivide(B, A, L)
"fail"
```
