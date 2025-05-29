```Julia
catalysis : [T⁻¹N], [T⁻¹N], [T⁻¹N], [T⁻¹N], [T⁻¹N]
catalysis(U::UnitSystem,S::UnitSystem) = molaramount(U,S)/time(U,S)
catalysis(v::Real,U::UnitSystem,S::UnitSystem) = v/catalysis(U,S)
T⁻¹N [ħ⁻¹𝘤²mₑ²Mᵤ⁻¹ϕ⁻¹g₀⁻¹] Unified
```

Catalytic activity or `molaramount` per `time` (kat, mol⋅s⁻¹), unit conversion factor.

```Julia
julia> catalysis(English,Metric) # kat⋅s⋅lb-mol⁻¹
lb⋅2³5³ = 453.59237 [mol]/[lb-mol] English -> Metric
```
