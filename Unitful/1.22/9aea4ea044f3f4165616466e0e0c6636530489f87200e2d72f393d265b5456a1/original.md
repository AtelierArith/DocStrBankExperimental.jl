```
dimension(x::Quantity{T,D}) where {T,D}
dimension(::Type{Quantity{T,D,U}}) where {T,D,U}
```

Returns a [`Unitful.Dimensions`](@ref) object `D` corresponding to the dimensions of quantity `x`. For a dimensionless [`Unitful.Quantity`](@ref), a `Unitful.Dimensions{()}` object is returned (`NoDims`).

Examples:

```jldoctest
julia> dimension(1.0u"m")
𝐋

julia> typeof(dimension(1.0u"m/μm"))
Unitful.Dimensions{()}
```
