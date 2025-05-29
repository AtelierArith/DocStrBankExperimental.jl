```
trans(dict::AbstractDict, len::Int64)
```

辞書 `dict` からサイズ `len` × `len` の隣接行列に変換します。

# 例

```jldoctest
julia> d = Dict((1, 2) => 5, (2, 3) => -1)

julia> trans(d, 4)
4×4 Array{Float64,2}:
 0.0   5.0   0.0  0.0
 5.0   0.0  -1.0  0.0
 0.0  -1.0   0.0  0.0
 0.0   0.0   0.0  0.0
```
