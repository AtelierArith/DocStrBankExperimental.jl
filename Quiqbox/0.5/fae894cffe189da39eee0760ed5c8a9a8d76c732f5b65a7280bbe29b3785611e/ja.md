```
genSpatialPoint(point::Union{Tuple{ParamBox{T}, Vararg{ParamBox{T}}}, 
                             AbstractVector{<:ParamBox{T}}}, 
                marker::Symbol=:point) where {T} -> 
SpatialPoint{T}
```

[`ParamBox`](@ref)のコレクションを[`SpatialPoint`](@ref)に変換します。
