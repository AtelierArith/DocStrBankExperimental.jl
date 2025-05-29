```Julia
stokes(U::UnitSystem) = diffusivity(𝟏,U,Gauss)
```

`diffusivity`のメートル単位 (m²⋅s⁻¹ または ft²⋅s⁻¹)。

```Julia
julia> stokes(Metric) # m²⋅s⁻¹
0.00010000000000000002

julia> stokes(CGS) # cm²⋅s⁻¹
1

julia> stokes(English) # ft²⋅s⁻¹
0.0010763910416709723
```
