```Julia
lunardistance(U::UnitSystem) = length(𝟏,U,IAUE)
```

地球と月の標準距離 (m または ft)。

```Julia
julia> lunardistance(Metric) # m
3.8439900000000006e8

julia> lunardistance(Nautical) # nm
207275.31408933675

julia> lunardistance(Metric)/lightspeed(Metric) # s
1.2822170463007447
```
