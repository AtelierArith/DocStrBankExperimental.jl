```
macro us_str(unit)
```

String macro to easily recall U.S. customary units located in the `UnitfulUS` package. Although all unit symbols in that package are suffixed with `_us`, the suffix should not be used when using this macro.

Note that what goes inside must be parsable as a valid Julia expression.

Examples:

```jldoctest
julia> 1.0us"tbsp"
1.0 m s^-1

julia> 1.0us"syd" - 1.0u"yd"
1.0 m N
```
