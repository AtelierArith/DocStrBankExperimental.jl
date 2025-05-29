```
band(i)
```

バンド行列の `i` 番目のバンドを表します。

```jldoctest
julia> using BandedMatrices

julia> A = BandedMatrix(0=>1:4, 1=>5:7, -1=>8:10)
4×4 BandedMatrix{Int64} with bandwidths (1, 1):
 1  5   ⋅  ⋅
 8  2   6  ⋅
 ⋅  9   3  7
 ⋅  ⋅  10  4

julia> A[band(1)]
3-element Vector{Int64}:
 5
 6
 7

julia> A[band(0)]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> A[band(-1)]
3-element Vector{Int64}:
  8
  9
 10
```
