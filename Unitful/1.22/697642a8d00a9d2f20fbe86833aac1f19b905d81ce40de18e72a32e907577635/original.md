```
unit(x::Number)
```

Returns the [`NoUnits`](@ref) object to indicate that ordinary numbers have no units. The unit is displayed as an empty string.

Examples:

```jldoctest
julia> typeof(unit(1.0))
Unitful.FreeUnits{(), NoDims, nothing}

julia> typeof(unit(Float64))
Unitful.FreeUnits{(), NoDims, nothing}

julia> unit(1.0) == NoUnits
true
```
