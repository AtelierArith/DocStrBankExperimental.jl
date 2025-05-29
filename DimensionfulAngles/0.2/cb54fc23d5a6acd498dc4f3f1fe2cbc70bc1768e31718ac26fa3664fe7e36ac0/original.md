```
macro ua_str(unit)
```

String macro to easily recall units with angular dimension located in the `DimensionfulAngles` package. Although all unit symbols in that package are suffixed with `ᵃ`, the suffix should not be used when using this macro.

Note that what goes inside must be parsable as a valid Julia expression.

# Examples

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> 1.0ua"turn"
1.0 τ

julia> 1.0ua"rad" - 1.0ua"°"
0.9825467074800567 rad
```
