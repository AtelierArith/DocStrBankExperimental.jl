```Julia
amagat(U::UnitSystem) = loschmidt(U)/avogadro(U)
molarity : [L⁻³N], [L⁻³N], [L⁻³N], [L⁻³N], [L⁻³N]
L⁻³N⋅(kB⁻¹R∞⁻³α⁶μₑᵤ⁻¹T₀⁻¹atm⋅τ⁻³2⁻³ = 2.8202760171(26) × 10⁻⁹) [ħ⁻³𝘤³mₑ⁴Mᵤ⁻¹ϕ⁻³g₀⁻³] Unified
```

Number of moles of an ideal gas in a unit volume (mol⋅m⁻³ or lb-mol⋅ft⁻³).

```Julia
julia> amagat(Metric) # mol⋅m⁻³
kB⁻¹𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹T₀⁻¹atm⋅2⁴5³ = 44.615033390(14) [m⁻³mol] Metric

julia> amagat(SI2019) # mol⋅m⁻³
kB⁻¹NA⁻¹T₀⁻¹atm = 44.615033405470314 [m⁻³mol] SI2019

julia> amagat(English) # slug-mol⋅ft⁻³
kB⁻¹𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹ft³lb⁻¹T₀⁻¹atm⋅2 = 0.00278522554558(86) [ft⁻³lb-mol] English
```
