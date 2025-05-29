```Julia
mpge(U::UnitSystem) = mile(U)/gasgallon(U)
nonstandard : [F⁻¹], [F⁻¹], [M⁻¹L⁻¹T²], [M⁻¹L⁻¹T²], [M⁻¹L⁻¹T²]
F⁻¹⋅(𝘩⋅𝘤⋅R∞²α⁻⁴ft⋅lb⁻¹Ωᵢₜ⋅Vᵢₜ⁻²τ⋅2⁻²5⁻⁷11⋅19⁻¹43 = 2.8368673134(17) × 10⁻⁶) [ħ⋅𝘤⁻³mₑ⁻²ϕ⋅g₀²] Unified
```

Equivalent `mile` per `gasgallon` reference unit of `length` per `energy` (N⁻¹ or lb⁻¹).

```Julia
julia> mpge(Metric) # N⁻¹
ft⋅lb⁻¹Ωᵢₜ⋅Vᵢₜ⁻²2⁻⁴5⁻⁷11⋅19⁻¹43 = 1.3380584481180184×10⁻⁵ [N⁻¹] Metric

julia> mpge(CGS) # dyn⁻¹
ft⋅lb⁻¹Ωᵢₜ⋅Vᵢₜ⁻²2⁻⁹5⁻¹²11⋅19⁻¹43 = 1.3380584481180183×10⁻¹⁰ [dyn⁻¹] Gauss

julia> mpge(English) # lb⁻¹
g₀⋅ft⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻⁴5⁻⁷11⋅19⁻¹43 = 5.95198051140049×10⁻⁵ [lbf⁻¹] English
```
