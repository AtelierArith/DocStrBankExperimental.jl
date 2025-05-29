```Julia
kelvin(U::UnitSystem) = temperature(𝟏,U,Metric)
```

Metric unit of `temperature` (K or °R).

```Julia
julia> kelvin(Metric) # K
1

julia> kelvin(SI2019) # K
0.9999999996562561

julia> kelvin(British) # °R
1.7999999999999998
```
