```Julia
mps(U::UnitSystem) = mile(U)/second(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹ft⋅2⁵3⋅5⋅11 = 5.368193752225748×10⁻⁶) [𝘤] Unified
```

Miles per second unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> mps(KKH) # km⋅h⁻¹
ft⋅2⁶3³11 = 5793.638400000001 [km⋅h⁻¹] KKH

julia> mps(MPH) # mi⋅h⁻¹
2⁴3²5² = 3600.0 [mi⋅h⁻¹] MPH

julia> mps(Nautical) # nm⋅h⁻¹
g₀¹ᐟ²ft⋅GME⁻¹ᐟ²τ⁻¹2¹⁴3⁶5⁵11 = 3124.0409550(31) [nm⋅h⁻¹] Nautical
```
