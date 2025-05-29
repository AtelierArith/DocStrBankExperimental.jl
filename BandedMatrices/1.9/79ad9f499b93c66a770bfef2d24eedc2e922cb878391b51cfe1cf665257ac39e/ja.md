```
rowrange(A, i::Integer)
```

`i`-行目に対応する埋められたバンドの列の範囲を返します。

# 例

```jldoctest
julia> A = BandedMatrix(0=>1:4, 1=>5:7)
4×4 BandedMatrix{Int64} with bandwidths (0, 1):
 1  5  ⋅  ⋅
 ⋅  2  6  ⋅
 ⋅  ⋅  3  7
 ⋅  ⋅  ⋅  4

julia> rowrange(A, 1)
1:2

julia> rowrange(A, 4)
4:4
```
