```Julia
diopter(U::UnitSystem) = angularwavenumber(𝟏,U,Metric)
```

Metric unit of `angularwavenumber` or curvature (m⁻¹ or ft⁻¹).

```Julia
julia> diopter(Metric) # m⁻¹
1

julia> diopter(CGS) # cm⁻¹
0.010000000000000002

julia> diopter(English) # ft⁻¹
0.3048
```
