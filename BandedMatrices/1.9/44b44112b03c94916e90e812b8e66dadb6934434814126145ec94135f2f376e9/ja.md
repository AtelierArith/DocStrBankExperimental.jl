```
colrange(A, i::Integer)
```

`i`-番目の列に対応する埋められたバンドの行の範囲を返します。

# 例

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
