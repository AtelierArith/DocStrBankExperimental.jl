```
bhattDist(arr::Array{T, 1}, h::Array{T, 1}) where {T <: Number}
```

# 説明

バッタチャリヤ距離。

# 例

```
julia> bhattDist(collect(1:10), fill(5, 10))
-3.936532135073928
```

参照: [`euclDist`](@ref), [`amplitude`](@ref)
