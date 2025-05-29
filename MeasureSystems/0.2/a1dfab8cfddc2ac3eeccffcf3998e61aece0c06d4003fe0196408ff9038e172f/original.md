```Julia
reyn(U::UnitSystem) = viscosity(𝟏,U,IPS)
viscosity : [FL⁻²T], [FL⁻²T], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹]
FL⁻²T⋅(𝘩⁻¹R∞⁻³α⁶g₀⋅ft⁻²lb⋅τ⁻²2⋅3² = 3.7648025968(35)) [ħ⁻²𝘤³mₑ³ϕ⁻²g₀⁻³] Unified
```

IPS unit of `viscosity` named after Reynolds (kg⋅m⁻¹⋅s⁻¹ or lb⋅s⋅ft⁻²).

```Julia
julia> reyn(Metric) # kg⋅m⁻¹⋅s⁻¹
g₀⋅ft⁻²lb⋅2⁴3² = 6894.75729316836 [Pa⋅s] Metric

julia> reyn(CGS) # g⋅cm⁻¹⋅s⁻¹
g₀⋅ft⁻²lb⋅2⁵3²5 = 68947.5729316836 [P] Gauss

julia> reyn(English) # lb⋅s⋅ft⁻²
2⁴3² = 144.0 [lbf⋅ft⁻²s] English
```
