```
Collar(table; [holeid], [x], [y], [z])
```

The collar `table` stores the `x`, `y`, `z` coordinates (usually in meters) of the head of the drill holes with specified `holeid`.

Common column names are searched in the `table` when keyword arguments are ommitted.

## Examples

```julia
Collar(table, holeid="BHID", x="EASTING", y="NORTHING")
Collar(table, x="XCOLLAR", y="YCOLLAR", z="ZCOLLAR")
```

See also [`Survey`](@ref), [`Interval`](@ref).
