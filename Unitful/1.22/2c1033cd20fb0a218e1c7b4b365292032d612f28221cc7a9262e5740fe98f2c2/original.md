```
@u_str(unit)
```

String macro to easily recall units, dimensions, or quantities defined in unit modules that have been registered with [`Unitful.register`](@ref).

If the same symbol is used for a [`Unitful.Units`](@ref) object defined in different modules, then the symbol found in the most recently registered module will be used.

Note that what goes inside must be parsable as a valid Julia expression. In other words, `u"N m"` will fail if you intended to write `u"N*m"`.

Examples:

```jldoctest
julia> 1.0u"m/s"
1.0 m s^-1

julia> 1.0u"N*m"
1.0 m N

julia> u"m,kg,s"
(m, kg, s)

julia> typeof(1.0u"m/s")
Quantity{Float64, 𝐋 𝐓^-1, Unitful.FreeUnits{(m, s^-1), 𝐋 𝐓^-1, nothing}}

julia> u"ħ"
1.0545718176461565e-34 J s
```
