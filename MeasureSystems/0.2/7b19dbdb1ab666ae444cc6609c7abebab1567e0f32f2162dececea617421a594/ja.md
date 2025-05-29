```Julia
poise(U::UnitSystem) = viscosity(𝟏,U,Gauss)
viscosity : [FL⁻²T], [FL⁻²T], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹]
FL⁻²T⋅(𝘩⁻¹R∞⁻³α⁶τ⁻²2⁻⁴5⁻¹ = 5.4603845163(50) × 10⁻⁵) [ħ⁻²𝘤³mₑ³ϕ⁻²g₀⁻³] Unified
```

`viscosity`のメートル法単位 (kg⋅m⁻¹⋅s⁻¹ または lb⋅s⋅ft⁻²)。

```Julia
julia> poise(Metric) # kg⋅m⁻¹⋅s⁻¹
2⁻¹5⁻¹ = 0.1 [Pa⋅s] Metric

julia> poise(CGS) # g⋅cm⁻¹⋅s⁻¹
𝟏 = 1.0 [P] Gauss

julia> poise(English) # lb⋅s⋅ft⁻²
g₀⁻¹ft²lb⁻¹2⁻¹5⁻¹ = 0.002088543423315013 [lbf⋅ft⁻²s] English
```
