```Julia
einstein(U::UnitSystem) = 𝟐^2*τ*gravitation(U)/lightspeed(U)^4
nonstandard : [FM⁻²L⁻²T⁴], [F⁻¹], [M⁻¹L⁻¹T²], [M⁻¹L⁻¹T²], [M⁻¹L⁻¹T²]
FM⁻²L⁻²T⁴⋅(𝘩²𝘤⁻²R∞²α⁻⁴mP⁻²τ⋅2⁴ = 4.402779(97) × 10⁻⁴⁴) [ħ⋅𝘤⁻³mₑ⁻²ϕ] 統一

```

アインシュタインの重力定数（s⋅²⋅m⁻¹⋅kg⁻¹）アインシュタイン場の方程式から。

```Julia
julia> einstein(Metric) # s²⋅m⁻¹⋅kg⁻¹
𝘩⋅𝘤⁻³mP⁻²2² = 2.076648(46) × 10⁻⁴³ [N⁻¹] メトリック

julia> einstein(IAU) # day²⋅au⁻¹⋅M☉⁻¹
𝘤⁻⁴au⁴kG²τ³2⁻⁴⁰3⁻²⁰5⁻¹⁴ = 8.27497346775(66) × 10⁻¹² [M☉⁻¹au⁻¹D²] IAU☉
```
