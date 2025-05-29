```
Survey(table; [holeid], [at], [azm], [dip])
```

The survey `table` stores the `azm` and `dip` angles (usually in degrees) `at` each depth (usually in meters) along drill holes with specified `holeid`.

Common column names are searched in the `table` when keyword arguments are ommitted.

## Examples

```julia
Survey(table, holeid="BHID", at="DEPTH")
Survey(table, azm="AZIMUTH")
```

See also [`Collar`](@ref), [`Interval`](@ref).
