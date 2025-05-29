```
DecideZeroColumns(B, A)

Returns: a homalg matrix
```

Let B and A be matrices having the same number of rows and defined over the same ring R and S be the column span of A, i.e. the R-submodule of the free right module R(NrRows(A)×1) spanned by the columns of A. The result is a matrix B′ having the same shape as B, for which the i-th column B′*i is equivalent to the i-th column B*i of B modulo S, i.e. B′*i−B*i is an element of the column span S of A. Moreover, the column B′*i is zero, if and only if the column B*i is an element of S. So DecideZeroColumns decides which columns of B are zero modulo the columns of A.

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> B = HomalgMatrix([3, 1, 7, 1, 11, 1], 3, 2, ZZ)
[ 3   1]
[ 7   1]
[11   1]

julia> DecideZeroColumns(B, A)
[0   0]
[0   0]
[0   0]
```
