```Julia
foot(U::UnitSystem) = length(𝟏,U,English)
```

英語の`length`の単位（mまたはft）。

```Julia
julia> foot(Metric) # m
0.3048

julia> foot(Survey) # ftUS
0.999998

julia> foot(IPS) # in
11.999999999999996
```
