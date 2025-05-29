```Julia
molarconductivity : [F⁻¹T⁻¹Q²N⁻¹], [F⁻¹T⁻¹Q²N⁻¹], [M⁻¹L⁻¹TQ²N⁻¹], [TN⁻¹], [L²T⁻¹N⁻¹]
molarconductivity(U::UnitSystem,S::UnitSystem) = conductivity(U,S)*area(U,S)/molaramount(U,S)
molarconductivity(v::Real,U::UnitSystem,S::UnitSystem) = v/molarconductivity(U,S)
F⁻¹T⁻¹Q²N⁻¹ [ħ⋅𝘤⁻²μ₀⁻¹mₑ⁻²Mᵤ⋅ϕ⋅λ⁻¹αL⁻²g₀] 統一

`molarvolume` あたりの導電率または `molarconductivity` (S⋅m²⋅mol⁻¹)、単位変換係数。

```

Julia julia> molarconductivity(EMU,Metric) # S⋅m²⋅abΩ⋅cm⁻² 2⁷5⁷ = 1.0×10⁷ [kg⁻¹m⁻¹s²C²]/[s²] EMU -> Metric

julia> molarconductivity(ESU,Metric) # S⋅m²⋅statΩ⋅cm⁻² 𝘤⁻²2³5³ = 1.1126500560536184×10⁻¹⁴ [kg⁻¹m⁻¹s²C²]/[cm²] ESU -> Metric ```
