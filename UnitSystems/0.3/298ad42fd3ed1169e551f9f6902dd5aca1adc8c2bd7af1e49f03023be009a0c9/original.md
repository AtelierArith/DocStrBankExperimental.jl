```Julia
meridianmile(U::UnitSystem) = length(𝟐^4*𝟓^5/𝟑^3,U,Metric)
```

Historic nautical mile as defined by naive meridian assumption (m or ft).

```Julia
julia> meridianmile(Metric) # m
1851.851851851852

julia> meridianmile(English) # ft
6075.629435209487

julia> meridianmile(Nautical) # nm
0.9985540395253695
```
