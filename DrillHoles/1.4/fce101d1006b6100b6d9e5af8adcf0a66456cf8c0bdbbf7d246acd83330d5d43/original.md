```
Interval(table; [holeid], [from], [to])
```

The interval `table` stores the interval `from` a given depth `to` another greater depth (usually in meters), along drill holes with specified `holeid`. Besides the intervals, the `table` stores measurements of variables such as grades, mineralization domains, geological interpretations, etc.

Common column names are searched in the `table` when keyword arguments are ommitted.

## Examples

```julia
Interval(table, holeid="BHID", from="START", to="FINISH")
Interval(table, from="BEGIN", to="END")
```

See also [`Collar`](@ref), [`Survey`](@ref).
