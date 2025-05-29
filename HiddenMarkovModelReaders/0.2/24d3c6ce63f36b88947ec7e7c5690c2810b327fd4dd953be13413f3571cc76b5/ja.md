```
euclDist(arr::Array{T, 1}, h::Array{T, 1}) where {T <: Number}
```

# 説明

ユークリッド距離。

# 例

```
julia> euclDist(collect(1:10), fill(5, 10))
9.219544457292887
```

参照: [`bhattDist`](@ref), [`amplitude`](@ref)
