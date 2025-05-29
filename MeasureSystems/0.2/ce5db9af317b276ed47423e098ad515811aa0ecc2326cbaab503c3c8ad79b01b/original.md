```Julia
knot(U::UnitSystem) = nauticalmile(U)/hour(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2⁻⁹3⁻⁵5⁻⁴ = 1.7183493525(17) × 10⁻⁹) [𝘤] Unified
```

Nautical miles per hour unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> knot(Metric) # m⋅s⁻¹
g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2⁻⁹3⁻⁵5⁻⁴ = 0.51514817608(52) [m⋅s⁻¹] Metric

julia> knot(KKH) # km⋅h⁻¹
g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2⁻⁸3⁻³5⁻⁵ = 1.8545334339(19) [km⋅h⁻¹] KKH

julia> knot(MPH) # mi⋅h⁻¹
g₀⁻¹ᐟ²ft⁻¹GME¹ᐟ²τ⋅2⁻¹⁰3⁻⁴5⁻³11⁻¹ = 1.1523536509(12) [mi⋅h⁻¹] MPH
```
