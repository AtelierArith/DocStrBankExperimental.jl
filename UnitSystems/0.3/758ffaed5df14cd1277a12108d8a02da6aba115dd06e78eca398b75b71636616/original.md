```Julia
rankine(U::UnitSystem) = temperature(𝟏,U,English)
```

English unit of `temperature` (K or °R).

```Julia
julia> rankine(Metric) # K
0.5555555555555556

julia> rankine(SI2019) # K
0.5555555553645868

julia> rankine(British) # °R
1
```
