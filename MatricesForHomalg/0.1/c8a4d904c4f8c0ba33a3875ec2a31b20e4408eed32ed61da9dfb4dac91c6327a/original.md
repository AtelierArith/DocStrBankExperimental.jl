```
SyzygiesOfRows(A, N)

Returns: a homalg matrix
```

Let R be the ring over which A is defined. The matrix of relative row syzygies SyzygiesOfRows(A, N) is a matrix whose rows span the left kernel of A modulo N, i.e. the R-submodule of the free left module R(1×NrRows(A)) consisting of all rows K satisfying KA+LN=0 for some row L∈R(1×NrRows(N)).

```jldoctest
julia> A = HomalgMatrix(1:9, 3, 3, ZZ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> N = HomalgMatrix(2:10, 3, 3, ZZ)
[2   3    4]
[5   6    7]
[8   9   10]

julia> SyzygiesOfRows(A, N)
[1   0   2]
[0   1   2]
[0   0   3]

julia> SyzygiesOfRows(A,A)
[1   0   0]
[0   1   0]
[0   0   1]
```
