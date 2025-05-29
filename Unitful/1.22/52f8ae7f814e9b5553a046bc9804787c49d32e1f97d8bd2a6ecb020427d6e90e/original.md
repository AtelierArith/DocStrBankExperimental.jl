```
dimension(x::Number)
dimension(x::Type{T}) where {T<:Number}
```

Returns a `Unitful.Dimensions{()}` object to indicate that ordinary numbers are dimensionless. This is a singleton, which we export as `NoDims`. The dimension is displayed as an empty string.

Examples:

```jldoctest
julia> typeof(dimension(1.0))
Unitful.Dimensions{()}

julia> typeof(dimension(Float64))
Unitful.Dimensions{()}

julia> dimension(1.0) == NoDims
true
```
