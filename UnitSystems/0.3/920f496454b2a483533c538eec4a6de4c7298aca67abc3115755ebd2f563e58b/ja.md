```Julia
diopter(U::UnitSystem) = angularwavenumber(𝟏,U,Metric)
```

`angularwavenumber` または曲率のメートル法単位 (m⁻¹ または ft⁻¹)。

```Julia
julia> diopter(Metric) # m⁻¹
1

julia> diopter(CGS) # cm⁻¹
0.010000000000000002

julia> diopter(English) # ft⁻¹
0.3048
```
