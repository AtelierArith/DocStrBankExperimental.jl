```Julia
abmho(U::UnitSystem) = conductance(𝟏,U,EMU)
conductance : [F⁻¹L⁻¹T⁻¹Q²], [F⁻¹L⁻¹T⁻¹Q²], [M⁻¹L⁻²TQ²], [L⁻¹T], [LT⁻¹]
F⁻¹L⁻¹T⁻¹Q²⋅(𝘃⋅τ⋅2³5² = 3.767303134617706×10¹¹) [𝘃⁻¹μ₀⁻¹λ⁻¹αL⁻²] 統一

電磁単位の `conductance` (S)。

```

Julia julia> abmho(Metric) # S 2⁹5⁹ = 1.0×10⁹ [S] メトリック

julia> abmho(EMU) # abS 𝟏 = 1.0 [cm⁻¹s] EMU

julia> abmho(ESU) # statS 𝘃²2⁴5⁴ = 8.987551787368175×10²⁰ [cm⋅s⁻¹] ESU ```
