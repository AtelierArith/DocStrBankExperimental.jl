```Julia
stokes(U::UnitSystem) = diffusivity(𝟏,U,Gauss)
diffusivity : [L²T⁻¹], [L²T⁻¹], [L²T⁻¹], [L²T⁻¹], [L²T⁻¹]
L²T⁻¹⋅(𝘤⁻¹R∞⋅α⁻²τ⋅2⁻³5⁻⁴ = 0.86379927371(26)) [ħ⋅mₑ⁻¹ϕ⋅g₀] Unified
```

`diffusivity`のメートル法単位 (m²⋅s⁻¹ または ft²⋅s⁻¹)。

```Julia
julia> stokes(Metric) # m²⋅s⁻¹
2⁻⁴5⁻⁴ = 0.0001 [m²s⁻¹] Metric

julia> stokes(CGS) # cm²⋅s⁻¹
𝟏 = 1.0 [St] Gauss

julia> stokes(English) # ft²⋅s⁻¹
ft⁻²2⁻⁴5⁻⁴ = 0.0010763910416709721 [ft²s⁻¹] English
```
