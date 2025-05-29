```
genSpatialPoint(point::Union{Tuple{ParamBox{T}, Vararg{ParamBox{T}}}, 
                             AbstractVector{<:ParamBox{T}}}, 
                marker::Symbol=:point) where {T} -> 
SpatialPoint{T}
```

Convert a collection of [`ParamBox`](@ref)s to a [`SpatialPoint`](@ref).
