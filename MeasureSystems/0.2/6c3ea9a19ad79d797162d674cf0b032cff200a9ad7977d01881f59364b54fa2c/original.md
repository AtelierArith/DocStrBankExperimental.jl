```Julia
roentgen(U::UnitSystem) = chargedensity(𝟏,U,ESU)/density(Constant(1.293),U,Metric)
exposure : [M⁻¹Q], [F⁻¹LT⁻²Q], [M⁻¹Q], [M⁻¹ᐟ²L¹ᐟ²], [M⁻¹ᐟ²L³ᐟ²T⁻¹]
M⁻¹Q/1.293 [ħ¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²mₑ⁻¹ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] Unified
```

Legacy unit of ionisation `exposure` (C⋅kg⁻¹ or C⋅lb⁻¹).

```Julia
julia> roentgen(Metric) # C⋅kg⁻¹
𝘤⁻¹2⁵5⁵/1.293 = 0.0002579768717696458 [kg⁻¹C] Metric

julia> roentgen(English) # C⋅lb⁻¹
𝘤⁻¹lb⋅2⁵5⁵/1.293 = 0.00011701634067117975 [lbm⁻¹C] English
```
