```
dimension(u::Units{U,D}) where {U,D}
```

Returns a [`Unitful.Dimensions`](@ref) object corresponding to the dimensions of the units, `D`. For a dimensionless combination of units, a `Unitful.Dimensions{()}` object is returned (`NoDims`).

Examples:

```jldoctest
julia> dimension(u"m")
𝐋

julia> typeof(dimension(u"m"))
Unitful.Dimensions{(Unitful.Dimension{:Length}(1//1),)}

julia> dimension(u"m/km")
NoDims
```
