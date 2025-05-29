```Julia
celsius(U::UnitSystem) = temperature(T₀,U,Metric)
```

Metric unit of `temperature` (K or °R).

```Julia
julia> celsius(Metric) # K
273.15

julia> celsius(SI2019) # K
273.1499999061063

julia> celsius(British) # °R
491.66999999999996
```
