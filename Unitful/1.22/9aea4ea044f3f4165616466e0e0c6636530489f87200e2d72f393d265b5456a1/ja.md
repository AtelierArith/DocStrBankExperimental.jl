```
dimension(x::Quantity{T,D}) where {T,D}
dimension(::Type{Quantity{T,D,U}}) where {T,D,U}
```

指定された量 `x` の次元に対応する [`Unitful.Dimensions`](@ref) オブジェクト `D` を返します。次元のない [`Unitful.Quantity`](@ref) に対しては、`Unitful.Dimensions{()}` オブジェクト（`NoDims`）が返されます。

例:

```jldoctest
julia> dimension(1.0u"m")
𝐋

julia> typeof(dimension(1.0u"m/μm"))
Unitful.Dimensions{()}
```
