```Julia
rotationalinertia : [ML²], [FLT²], [ML²], [ML²], [ML²]
rotationalinertia(U::UnitSystem,S::UnitSystem) = mass(U,S)*area(U,S)
rotationalinertia(v::Real,U::UnitSystem,S::UnitSystem) = v/rotationalinertia(U,S)
ML² [ħ²𝘤⁻²mₑ⁻¹ϕ²g₀²] Unified
```

Moment of inertia or `rotationalinertia` (kg⋅m²), unit conversion factor.

```Julia
julia> rotationalinertia(CGS,Metric) # kg⋅m²⋅g⁻¹⋅cm⁻²
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [kg⋅m²]/[g⋅cm²] Gauss -> Metric

julia> rotationalinertia(CGS,British) # slug⋅ft²⋅g⁻¹⋅cm⁻²
g₀⁻¹ft⁻¹lb⁻¹2⁻⁷5⁻⁷ = 7.375621492772652×10⁻⁸ [lb⋅ft⋅s²]/[g⋅cm²] Gauss -> British

julia> rotationalinertia(English,Metric) # kg⋅m²⋅lb⁻¹⋅ft⁻²
ft²lb = 0.042140110093804806 [kg⋅m²]/[lbm⋅ft²] English -> Metric
```
