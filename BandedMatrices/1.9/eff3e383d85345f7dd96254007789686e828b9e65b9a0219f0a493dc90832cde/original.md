```
BandRange
```

Represents the entries in a row/column inside the bands.

```jldoctest
julia> using BandedMatrices

julia> A = BandedMatrix(0=>1:4, 1=>5:7, -1=>8:10)
4×4 BandedMatrix{Int64} with bandwidths (1, 1):
 1  5   ⋅  ⋅
 8  2   6  ⋅
 ⋅  9   3  7
 ⋅  ⋅  10  4

julia> A[2, BandRange]
3-element Vector{Int64}:
 8
 2
 6
```
