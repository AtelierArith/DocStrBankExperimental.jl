```Julia
fpm(U::UnitSystem) = feet(U)/minute(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹ft⋅2⁻²3⁻¹5⁻¹ = 1.6945056036066124×10⁻¹¹) [𝘤] Unified
```

フィート毎分の `speed` の単位 (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> fpm(CGS) # cm⋅s⁻¹
ft⋅3⁻¹5 = 0.508 [cm⋅s⁻¹] Gauss

julia> fpm(IPS) # in⋅s⁻¹
5⁻¹ = 0.2 [in⋅s⁻¹] IPS

julia> fpm(English) # ft⋅s⁻¹
2⁻²3⁻¹5⁻¹ = 0.016666666666666666 [ft⋅s⁻¹] English
```
