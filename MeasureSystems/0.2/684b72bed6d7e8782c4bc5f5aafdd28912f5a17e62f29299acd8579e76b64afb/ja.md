```Julia
ips(U::UnitSystem) = inch(U)/second(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹ft⋅2⁻²3⁻¹ = 8.472528018033061×10⁻¹¹) [𝘤] Unified
```

インチ毎秒の `speed` の単位 (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> ips(CGS) # cm⋅s⁻¹
ft⋅3⁻¹5² = 2.5399999999999996 [cm⋅s⁻¹] Gauss

julia> ips(English) # ft⋅s⁻¹
2⁻²3⁻¹ = 0.08333333333333333 [ft⋅s⁻¹] English
```
