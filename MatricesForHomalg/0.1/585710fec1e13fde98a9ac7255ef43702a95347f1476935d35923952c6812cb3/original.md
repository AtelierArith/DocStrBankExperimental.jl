```
DecideZeroRows(B, A)

Returns: a homalg matrix
```

Let B and A be matrices having the same number of columns and defined over the same ring R and S be the row span of A, i.e. the R-submodule of the free left module R(1×NrColumns(A)) spanned by the rows of A. The result is a matrix B′ having the same shape as B, for which the i-th row B′^i is equivalent to the i-th row B^i of B modulo S, i.e. B′^i−B^i is an element of the row span S of A. Moreover, the row B′^i is zero, if and only if the row B^i is an element of S. So DecideZeroRows decides which rows of B are zero modulo the rows of A.

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> A′ = DecideZeroRows(B, A)
[0   1]
[0   1]
[0   1]

julia> RightDivide(B, A)
"fail"

julia> RightDivide(B - A′, A)
[0   -1   1]
[0   -2   2]
[0   -3   3]

julia> DecideZeroRows(A, A)
[0   0]
[0   0]
[0   0]

julia> C = HomalgMatrix([4, 6, 2, 2], 2, 2, ZZ)
[4   6]
[2   2]

julia> DecideZeroRows(C, A)
[0   0]
[0   0]

julia> DecideZeroRows(A, C)
[1   0]
[1   0]
[1   0]
```
