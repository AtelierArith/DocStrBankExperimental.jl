```
SyzygiesOfColumns(A, N)

Returns: a homalg matrix
```

Let R be the ring over which M is defined. The matrix of relative column syzygies SyzygiesOfColumns(A,N) is a matrix whose columns span the right kernel of A modulo N, i.e. the R-submodule of the free right module R(NrColumns(A)×1)consisting of all columns K satisfying AK+NL=0 for some column L∈R(NrColumns(N)×1).

```jldoctest
julia> A = HomalgMatrix(1:6, 3, 2, ZZ)
[1   2]
[3   4]
[5   6]

julia> N = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> SyzygiesOfColumns(A, N)
[1   0]
[0   1]
```
