```
SpatialPoint{T, D, PT} <: AbstractSpatialPoint{T, D}
```

A `D`-dimensional spatial point.

≡≡≡ Field(s) ≡≡≡

`param::PT`: A `Tuple` of [`ParamBox`](@ref)s as the components of the spatial coordinate.

`marker::Symbol`: A marker that indicates the purpose or meaning of the constructed  `SpatialPoint`. The default marker is set to `:point`.

≡≡≡ Initialization Method(s) ≡≡≡

```
SpatialPoint(pbs::Union{Tuple{Quiqbox.ParamBox{T, :X, Fx}} where Fx, Tuple{Quiqbox.ParamBox{T, :X, Fx}, Quiqbox.ParamBox{T, :Y, Fy}} where {Fx, Fy}, Tuple{Quiqbox.ParamBox{T, :X, Fx}, Quiqbox.ParamBox{T, :Y, Fy}, Quiqbox.ParamBox{T, :Z, Fz}} where {Fx, Fy, Fz}} where T) -> SpatialPoint
```
