```Julia
inch(U::UnitSystem) = length(𝟏,U,IPS)
```

英語の単位の `length` (m または ft)。

```Julia
julia> inch(Metric) # m
0.025400000000000002

julia> inch(English) # ft
0.08333333333333334

julia> inch(IPS) # in
1
```
