```
SyzygiesOfRows(A)
```

Return a homalg matrix. Let R be the ring over which A is defined (R:= HomalgRing(A)). The matrix of row syzygies SyzygiesGeneratorsOfRows(A) is a matrix whose rows span the left kernel of A, i.e. the R-submodule of the free left module R(1xNrRows(A)) consisting of all rows X satisfying XA=0

```jldoctest
julia> A = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> S = SyzygiesOfRows(A)
[1   -2   1]

julia> S*A
[0   0]
```
