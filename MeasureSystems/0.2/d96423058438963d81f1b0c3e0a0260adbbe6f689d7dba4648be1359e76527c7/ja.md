```Julia
vacuumpermittivity(U::UnitSystem) = 𝟏/vacuumpermeability(U)/(lightspeed(U)*lorentz(U))^2
permittivity : [F⁻¹L⁻²Q²R], [F⁻¹L⁻²Q²], [M⁻¹L⁻³T²Q²], [L⁻²T²], [𝟙]
F⁻¹L⁻²Q²R [𝘃⁻²μ₀⁻¹αL⁻²] 統一

古典真空の誘電率定数 `ε₀` (C²⋅N⁻¹⋅m⁻²)。

```

Julia julia> vacuumpermittivity(Metric) # F⋅m⁻¹ 𝘃⁻²τ⁻¹2⁶5⁷ = 8.854187817620389×10⁻¹² [F⋅m⁻¹] Metric

julia> vacuumpermittivity(Conventional) # F⋅m⁻¹ 𝘃⁻¹α⁻¹RK90⁻¹2⁻¹ = 8.8541879703(14) × 10⁻¹² [F⋅m⁻¹] Conventional

julia> vacuumpermittivity(CODATA) # F⋅m⁻¹ 𝘃⁻¹α⁻¹RK⁻¹2⁻¹ = 8.8541878141(24) × 10⁻¹² [F⋅m⁻¹] CODATA

julia> vacuumpermittivity(SI2019) # F⋅m⁻¹ 𝘩⁻¹𝘃⁻¹𝘦²α⁻¹2⁻¹ = 8.8541878128(14) × 10⁻¹² [F⋅m⁻¹] SI2019

julia> vacuumpermittivity(International) # F⋅m⁻¹ 𝘃⁻²Ωᵢₜ⋅τ⁻¹2⁶5⁷ = 8.85857064059011×10⁻¹² [F⋅m⁻¹] International

julia> vacuumpermittivity(EMU) # abF⋅cm⁻¹ 𝘃⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻²s²] EMU

julia> vacuumpermittivity(ESU) # statF⋅cm⁻¹ 𝟏 = 1.0 [𝟙] ESU

julia> vacuumpermittivity(SI2019)/elementarycharge(SI2019) # 𝘦²⋅eV⁻¹⋅m⁻¹ 𝘩⁻¹𝘃⁻¹𝘦⋅α⁻¹2⁻¹ = 5.52634935805(85) × 10⁷ [kg⁻¹m⁻³s²C] SI2019 ```
