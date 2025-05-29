```
colrange(A, i::Integer)
```

Return the range of rows in the `i`-th column that correspond to filled bands.

# Examples

```jldoctest
julia> A = BandedMatrix(0=>1:4, 1=>5:7)
4×4 BandedMatrix{Int64} with bandwidths (0, 1):
 1  5  ⋅  ⋅
 ⋅  2  6  ⋅
 ⋅  ⋅  3  7
 ⋅  ⋅  ⋅  4

julia> colrange(A, 1)
1:1

julia> colrange(A, 3)
2:3
```
