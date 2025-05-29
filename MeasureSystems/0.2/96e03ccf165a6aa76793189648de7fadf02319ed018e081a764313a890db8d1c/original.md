```Julia
gforce(U::UnitSystem) = specificforce(𝟏,U,English)
specificforce : [FM⁻¹], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
FM⁻¹⋅(𝘤⁻²R∞⁻¹α²g₀⋅τ⁻¹2⁻¹ = 4.2135265250(13) × 10⁻²⁹) [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻²] Unified
```

Standard gravity `specificforce` `g₀` at geodetic reference latitude (m⋅s⁻² or ft⋅s⁻²).

```Julia
julia> gforce(CGS) # gal
g₀⋅2²5² = 980.665 [gal] Gauss

julia> gforce(British) # ft⋅s⁻²
g₀⋅ft⁻¹ = 32.17404855643044 [ft⋅s⁻²] British

julia> gforce(English) # lbf⋅lbm⁻¹
𝟏 = 1.0 [g₀] English
```
