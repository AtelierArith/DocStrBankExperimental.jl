```Julia
inch(U::UnitSystem) = length(𝟏,U,IPS)
```

English unit of `length` (m or ft).

```Julia
julia> inch(Metric) # m
0.025400000000000002

julia> inch(English) # ft
0.08333333333333334

julia> inch(IPS) # in
1
```
