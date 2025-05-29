```Julia
siderealmonth(U::UnitSystem) = gaussianmonth(U)/√(𝟏+lunarmass(IAU))
time : [T], [T], [T], [T], [T]
T⋅1.68839128266e6 ± 0.00038 [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] Unified
```

Orbit `time` defined by standard `lunardistance` and the Earth-Moon system `mass` (s).

```Julia
julia> siderealmonth(Metric) # s
GME⁻¹ᐟ²τ⋅2⁹ᐟ²3⁹ᐟ²5⁹ᐟ²⋅1.68839128266(38) × 10⁶ = 2.3573807233(24) × 10⁶ [s] Metric

julia> siderealmonth(MPH) # h
GME⁻¹ᐟ²τ⋅2¹ᐟ²3⁵ᐟ²5⁵ᐟ²⋅1.68839128266(38) × 10⁶ = 654.82797870(67) [h] MPH

julia> siderealmonth(IAU) # D
GME⁻¹ᐟ²τ⋅2⁻⁵ᐟ²3³ᐟ²5⁵ᐟ²⋅1.68839128266(38) × 10⁶ = 27.284499112(28) [D] IAU☉
```
