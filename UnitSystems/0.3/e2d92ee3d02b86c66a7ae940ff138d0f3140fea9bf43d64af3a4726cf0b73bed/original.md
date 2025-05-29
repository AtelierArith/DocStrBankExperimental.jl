```Julia
kayser(U::UnitSystem) = wavenumber(𝟏,U,Gauss)
```

Metric unit of `wavenumber` or curvature (m⁻¹ or ft⁻¹).

```Julia
julia> kayser(Metric) # m⁻¹
99.99999999999999

julia> kayser(CGS) # cm⁻¹
1

julia> kayser(English) # ft⁻¹
30.48
```
