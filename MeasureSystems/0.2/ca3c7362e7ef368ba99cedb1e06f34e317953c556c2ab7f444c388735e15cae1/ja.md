```Julia
electrostatic(U::UnitSystem) = rationalization(U)/𝟐/τ/vacuumpermittivity(U)
nonstandard : [FL²Q⁻²], [FL²Q⁻²], [ML³T⁻²Q⁻²], [L²T⁻²], [𝟙]
FL²Q⁻²⋅(τ⁻¹2⁻¹ = 0.07957747154594767) [𝘤²μ₀⋅λ⋅αL²] 統一

クーロンの法則における静電比例定数 `kₑ` (N⋅m²⋅C⁻²)。

```

Julia julia> electrostatic(Metric) # N⋅m²⋅C⁻² 𝘃²2⁻⁷5⁻⁷ = 8.987551787368176×10⁹ [m⋅F⁻¹] メトリック

julia> electrostatic(CODATA) # N·m²⋅C⁻² 𝘃⋅α⋅RK⋅τ⁻¹ = 8.9875517909(25) × 10⁹ [m⋅F⁻¹] CODATA

julia> electrostatic(SI2019) # N·m²⋅C⁻² 𝘩⋅𝘃⋅𝘦⁻²α⋅τ⁻¹ = 8.9875517923(14) × 10⁹ [m⋅F⁻¹] SI2019

julia> electrostatic(Conventional) # N·m²⋅C⁻² 𝘃⋅α⋅RK90⋅τ⁻¹ = 8.9875516323(14) × 10⁹ [m⋅F⁻¹] 従来

julia> electrostatic(International) # N·m²⋅C⁻² 𝘃²Ωᵢₜ⁻¹2⁻⁷5⁻⁷ = 8.983105150318768×10⁹ [m⋅F⁻¹] 国際

julia> electrostatic(EMU) # dyn⋅cm²⋅abC⁻² 𝘃²2⁴5⁴ = 8.987551787368175×10²⁰ [erg⋅g⁻¹] EMU

julia> electrostatic(ESU) # dyn⋅cm²⋅statC⁻² 𝟏 = 1.0 [𝟙] ESU

julia> electrostatic(HLU) # dyn⋅cm²⋅hlC⁻² τ⁻¹2⁻¹ = 0.07957747154594767 [𝟙] ローレンツ・ヘビサイド ```
