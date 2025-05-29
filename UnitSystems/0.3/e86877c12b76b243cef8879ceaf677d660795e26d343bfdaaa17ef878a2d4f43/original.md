```Julia
foot(U::UnitSystem) = length(𝟏,U,English)
```

English unit of `length` (m or ft).

```Julia
julia> foot(Metric) # m
0.3048

julia> foot(Survey) # ftUS
0.999998

julia> foot(IPS) # in
11.999999999999996
```
