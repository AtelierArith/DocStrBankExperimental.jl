```Julia
thermalunit(U::UnitSystem) = kilocalorie(U)*𝟑^2/𝟓/lb
```

1 lbの水を1 Rankine（`BTU`）上昇させるのに必要な熱エネルギー（`International`単位）。

```Julia
julia> thermalunit(British) # ft⋅lb
778.1576129990755

julia> thermalunit(International) # J
1054.8659767441864

julia> thermalunit(Metric) # J
1055.0400583348664
```
