```Julia
specificvolume : [M⁻¹L³], [F⁻¹L⁴T⁻²], [M⁻¹L³], [M⁻¹L³], [M⁻¹L³]
specificvolume(U::UnitSystem,S::UnitSystem) = volume(U,S)/mass(U,S)
specificvolume(v::Real,U::UnitSystem,S::UnitSystem) = v/specificvolume(U,S)
M⁻¹L³ [ħ³𝘤⁻³mₑ⁻⁴ϕ³g₀³] Unified
```

Reciprocal `density` or `volume` per `mass` or `specificvolume` (m³⋅kg), unit conversion factor.

```Julia
julia> specificvolume(CGS,Metric) # g⋅m³⋅kg⁻¹⋅cm⁻³
2⁻³5⁻³ = 0.001 [kg⁻¹m³]/[g⁻¹cm³] Gauss -> Metric

julia> specificvolume(CGS,British) # kg⋅ft³⋅slug⁻¹⋅cm⁻³
g₀⋅ft⁻⁴lb⋅2⁻³5⁻³ = 0.5153788183931961 [lb⁻¹ft⁴s⁻²]/[g⁻¹cm³] Gauss -> British

julia> specificvolume(English,Metric) # lb⋅m³⋅kg⁻¹⋅ft⁻³
ft³lb⁻¹ = 0.062427960576144616 [kg⁻¹m³]/[lbm⁻¹ft³] English -> Metric
```
