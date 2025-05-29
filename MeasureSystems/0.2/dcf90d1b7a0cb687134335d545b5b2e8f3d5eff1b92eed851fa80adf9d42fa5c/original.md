```Julia
mph(U::UnitSystem) = mile(U)/hour(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹ft⋅2⋅3⁻¹5⁻¹11 = 1.4911649311738188×10⁻⁹) [𝘤] Unified
```

Miles per hour unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> mph(Metric) # m⋅s⁻¹
ft⋅2⋅3⁻¹5⁻¹11 = 0.44704 [m⋅s⁻¹] Metric

julia> mph(KKH) # km⋅h⁻¹
ft⋅2²3⋅5⁻²11 = 1.6093440000000003 [km⋅h⁻¹] KKH

julia> mph(Nautical) # nm⋅h⁻¹
g₀¹ᐟ²ft⋅GME⁻¹ᐟ²τ⁻¹2¹⁰3⁴5³11 = 0.86778915418(87) [nm⋅h⁻¹] Nautical
```
