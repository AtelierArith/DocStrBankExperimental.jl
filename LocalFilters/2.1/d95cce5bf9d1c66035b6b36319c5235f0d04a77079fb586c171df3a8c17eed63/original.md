```
LocalFilters.unit_range(r::Union{AbstractRange{<:Integer},CartesianIndices})
```

converts `r` into an `Int`-valued unit step index range. `r` may be a linear or a Cartesian index range. If `r` is a linear range, the absolute value of its step must be 1.

```
LocalFilters.unit_range(start::Integer, stop::Integer)
```

yields the `Int`-valued unit step range `Int(start):Int(stop)`.
