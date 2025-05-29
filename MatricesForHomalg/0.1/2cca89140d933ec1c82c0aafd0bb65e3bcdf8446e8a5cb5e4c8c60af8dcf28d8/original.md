```
SyzygiesOfColumns(A)
```

Return a homalg matrix. Let R be the ring over which A is defined (R:=HomalgRing(A)). The matrix of column syzygies SyzygiesGeneratorsOfColumns(A) is a matrix whose columns span the right kernel of A, i.e. the R-submodule of the free right module R(NrColumns(A)x1) consisting of all columns X satisfying AX=0

```jldoctest
julia> A = TransposedMatrix(HomalgMatrix(4:9, 3, 2, ZZ))
[4   6   8]
[5   7   9]

julia> S = SyzygiesOfColumns(A)
[ 1]
[-2]
[ 1]

julia> A*S
[0]
[0]
```
