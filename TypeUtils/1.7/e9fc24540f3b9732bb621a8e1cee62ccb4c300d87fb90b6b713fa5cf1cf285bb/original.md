```
to_same_type(x1, x2, ...) -> xp1, xp2, ...
```

converts instances `x1`, `x2`, ... to the same type. This method may be used instead of `promote(x1,x2,...)` which does not warrant that the converted values have the same type.

Example:

```julia
julia> using Unitful, TypeUtils

julia> promote(2, 3.0)
(2.0, 3.0)

julia> to_same_type(2, 3.0)
(2.0, 3.0)

julia> promote(2u"mm", 3.0)
(2.0 mm, 3.0)

julia> to_same_type(2u"mm", 3.0)
ERROR: ArgumentError: types `Quantity{Int64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}` and `Float64` cannot be converted to a common concrete type
Stacktrace:
 ...

julia> promote(2u"mm", 4.0u"nm")
(0.002 m, 4.0e-9 m)

julia> to_same_type(2u"mm", 4.0u"nm")
(0.002 m, 4.0e-9 m)
```

Also see [`to_same_concrete_type`](@ref).
