```
plate(size, conditions...)
```

Construct a WellPlate, specifying its size and conditions.

# Examples

```julia-repl
julia> plate(96, cellline = :Raji)
Plate with 96 wells with 8 rows and 12 columns
Conditions: [:cellline]
```

See also [`WellPlate`](@ref).
