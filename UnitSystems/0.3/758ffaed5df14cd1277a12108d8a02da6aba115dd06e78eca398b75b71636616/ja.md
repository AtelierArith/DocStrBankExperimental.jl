```Julia
rankine(U::UnitSystem) = temperature(𝟏,U,English)
```

英語単位の `temperature` (K または °R)。

```Julia
julia> rankine(Metric) # K
0.5555555555555556

julia> rankine(SI2019) # K
0.5555555553645868

julia> rankine(British) # °R
1
```
