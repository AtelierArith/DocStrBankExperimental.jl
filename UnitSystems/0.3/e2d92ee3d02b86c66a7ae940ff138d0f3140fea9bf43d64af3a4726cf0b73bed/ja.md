```Julia
kayser(U::UnitSystem) = wavenumber(𝟏,U,Gauss)
```

`wavenumber` または曲率のメートル法単位 (m⁻¹ または ft⁻¹)。

```Julia
julia> kayser(Metric) # m⁻¹
99.99999999999999

julia> kayser(CGS) # cm⁻¹
1

julia> kayser(English) # ft⁻¹
30.48
```
