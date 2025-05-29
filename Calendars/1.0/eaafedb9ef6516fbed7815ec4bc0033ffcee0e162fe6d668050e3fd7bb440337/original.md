```julia
ConvertOrdinalDate(num::DPart, from::String, to::String)
```

`num` is an ordinal date, i.e. an integer counting the ellapsed days  since the beginning of a calendrial epoch.

`from` and `to` are ordinal date names. Currently only the ordinal date names "EuroNum" and "JulianNum", respectively their acronyms EN, JN, are admissible.

Examples: Convert a Julian day number to an European day number.

```julia
julia> ConvertOrdinalDate(2440422, JN, EN) 
```

The European day number of the first crewed moon landing is 719000.

Convert an European day number to an Julian day number.

```julia
julia> ConvertOrdinalDate(719000, EN, JN) 
```

The Julian day number of the first crewed moon landing is 2440422.
