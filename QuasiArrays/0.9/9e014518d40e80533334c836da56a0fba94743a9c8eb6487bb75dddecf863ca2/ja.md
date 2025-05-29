```
QuasiDiagonal(V::AbstractQuasiVector)
```

`V`を対角成分とする行列を構築します。

# 例

```jldoctest
julia> V = [1, 2]
2-element Array{Int64,1}:
 1
 2

julia> QuasiDiagonal(V)
2×2 QuasiDiagonal{Int64,Array{Int64,1}}:
 1  ⋅
 ⋅  2
```
