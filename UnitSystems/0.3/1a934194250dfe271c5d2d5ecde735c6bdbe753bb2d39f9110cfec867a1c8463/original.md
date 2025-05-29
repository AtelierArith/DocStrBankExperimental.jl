```Julia
thermalunit(U::UnitSystem) = kilocalorie(U)*𝟑^2/𝟓/lb
```

Heat energy required to raise 1 lb of water by 1 Rankine (`BTU`) in `International` units.

```Julia
julia> thermalunit(British) # ft⋅lb
778.1576129990755

julia> thermalunit(International) # J
1054.8659767441864

julia> thermalunit(Metric) # J
1055.0400583348664
```
