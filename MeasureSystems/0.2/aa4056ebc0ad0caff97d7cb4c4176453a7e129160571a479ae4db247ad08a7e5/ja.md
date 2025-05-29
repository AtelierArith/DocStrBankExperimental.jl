```Julia
誘電率 : [F⁻¹L⁻²Q²R], [F⁻¹L⁻²Q²], [M⁻¹L⁻³T²Q²], [L⁻²T²], [𝟙]
誘電率(U::UnitSystem,S::UnitSystem) = 静電容量(U,S)*合理化(U,S)/長さ(U,S)
誘電率(v::Real,U::UnitSystem,S::UnitSystem) = v/誘電率(U,S)
F⁻¹L⁻²Q²R [𝘤⁻²μ₀⁻¹αL⁻²] 統一

絶対`誘電率`または`静電容量`あたりの`長さ` (F⋅m⁻¹)、単位変換係数。

```

Julia julia> 誘電率(EMU,Metric) # F⋅cm⋅abF⁻¹⋅m⁻¹ τ⁻¹2¹⁰5¹¹ = 7.957747154594768×10⁹ [F⋅m⁻¹]/[cm⁻²s²] EMU -> Metric

julia> 誘電率(ESU,Metric) # F⋅m⁼¹ 𝘤⁻²τ⁻¹2⁶5⁷ = 8.854187817620389×10⁻¹² [F⋅m⁻¹]/[𝟙] ESU -> Metric

julia> 誘電率(Metric,SI2019) # F⋅F⁻¹ 𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019 ```
