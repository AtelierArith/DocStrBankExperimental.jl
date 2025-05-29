```Julia
thermalresistance : [F⁻¹L⁻¹TΘ], [F⁻¹L⁻¹TΘ], [M⁻¹L⁻²T³Θ], [M⁻¹L⁻²T³Θ], [M⁻¹L⁻²T³Θ]
thermalresistance(U::UnitSystem,S::UnitSystem) = 1/thermalconductivity(U,S)/length(U,S)
thermalresistance(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalresistance(U,S)
F⁻¹L⁻¹TΘ [kB⁻¹ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] 統一

熱流に対する抵抗または `thermalresistance` (K⋅W⁻¹)、単位換算係数。

```

Julia julia> thermalresistance(Metric,SI2019) # K⋅K⁻¹ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [K]/[K] Metric -> SI2019

julia> thermalresistance(CGS,Metric) # erg⋅s⁻¹⋅W⁻¹ 2⁷5⁷ = 1.0×10⁷ [J⁻¹]/[erg⁻¹] Gauss -> Metric

julia> thermalresistance(English,Metric) # ft⋅lb⋅K⋅°R⁻¹⋅J⁻¹ g₀⁻¹ft⁻¹lb⁻¹3⁻²5 = 0.40975674959848074 [kg⁻¹m⁻²s²K]/[lbf⁻¹ft⁻¹°R] English -> Metric ```
