```Julia
触媒 : [T⁻¹N], [T⁻¹N], [T⁻¹N], [T⁻¹N], [T⁻¹N]
触媒(U::UnitSystem,S::UnitSystem) = molaramount(U,S)/time(U,S)
触媒(v::Real,U::UnitSystem,S::UnitSystem) = v/触媒(U,S)
T⁻¹N [ħ⁻¹𝘤²mₑ²Mᵤ⁻¹ϕ⁻¹g₀⁻¹] 統一

```

触媒活性または `molaramount` あたりの `time` (kat, mol⋅s⁻¹)、単位換算係数。

```Julia
julia> 触媒(English,Metric) # kat⋅s⋅lb-mol⁻¹
lb⋅2³5³ = 453.59237 [mol]/[lb-mol] English -> Metric
```
