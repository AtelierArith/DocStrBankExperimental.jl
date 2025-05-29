```Julia
ms(U::UnitSystem) = meter(U)/second(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹ = 3.3356409519815204×10⁻⁹) [𝘤] 統一

メートル毎秒の `speed` の単位 (m⋅s⁻¹ または ft⋅s⁻¹)。

```

Julia julia> ms(KKH) # km⋅h⁻¹ 2⋅3²5⁻¹ = 3.6 [km⋅h⁻¹] KKH

julia> ms(MPH) # mi⋅h⁻¹ ft⁻¹2⁻¹3⋅5⋅11⁻¹ = 2.236936292054402 [mi⋅h⁻¹] MPH

julia> ms(Nautical) # nm⋅h⁻¹ g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁹3⁵5⁴ = 1.9411890528(19) [nm⋅h⁻¹] Nautical ```
