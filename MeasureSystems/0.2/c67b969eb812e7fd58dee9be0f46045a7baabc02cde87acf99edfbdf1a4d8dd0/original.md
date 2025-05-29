```Julia
kmh(U::UnitSystem) = kilo(U)*meter(U)/hour(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹2⁻¹3⁻²5 = 9.265669311059779×10⁻¹⁰) [𝘤] Unified
```

Kilometers per hour unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> kmh(Metric) # m⋅s⁻¹
2⁻¹3⁻²5 = 0.2777777777777778 [m⋅s⁻¹] Metric

julia> kmh(MPH) # mi⋅h⁻¹
ft⁻¹2⁻²3⁻¹5²11⁻¹ = 0.6213711922373338 [mi⋅h⁻¹] MPH

julia> kmh(Nautical) # nm⋅h⁻¹
g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁸3³5⁵ = 0.53921918134(54) [nm⋅h⁻¹] Nautical
```
