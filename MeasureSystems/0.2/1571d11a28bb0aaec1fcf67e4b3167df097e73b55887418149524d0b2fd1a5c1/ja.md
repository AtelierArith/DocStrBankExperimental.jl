```Julia
電気変位 : [L⁻²QR], [L⁻²Q], [L⁻²Q], [M¹ᐟ²L⁻³ᐟ²], [M¹ᐟ²L⁻¹ᐟ²T⁻¹]
電気変位(U::UnitSystem,S::UnitSystem) = charge(U,S)*rationalization(U,S)/area(U,S)
電気変位(v::Real,U::UnitSystem,S::UnitSystem) = v/電気変位(U,S)
L⁻²QR [ħ⁻³ᐟ²𝘤³ᐟ²μ₀⁻¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²αL⁻¹g₀⁻²] 統一

電場の変位または表面 `電気変位` (C⋅m⁻²)、単位換算係数。

```

Julia julia> 電気変位(EMU,Metric) # C⋅cm²⋅abC⁻¹⋅m⁻² τ⁻¹2⁴5⁵ = 7957.747154594767 [m⁻²C]/[g¹ᐟ²cm⁻³ᐟ²] EMU -> Metric

julia> 電気変位(ESU,Metric) # C⋅cm²⋅statC⁻¹⋅m⁼² 𝘤⁻¹τ⁻¹2²5³ = 2.6544187294380724×10⁻⁷ [m⁻²C]/[g¹ᐟ²cm⁻¹ᐟ²s⁻¹] ESU -> Metric

julia> 電気変位(Metric,SI2019) # C⋅C⁻¹ 𝘩⁻¹ᐟ²𝘃¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019 ```
