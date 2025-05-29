```Julia
jovianyear(U::UnitSystem) = τ*day(U)*√(jupiterdistance(U)^3/solarmass(U)/gravitation(U))/√(𝟏+jupitermass(IAU))
time : [T], [T], [T], [T], [T]
T⋅1.321238687229e8 ± 0.0045 [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] Unified
```

Orbit `time` defined by `jupiterdistance` and the Sun-Jupiter system `mass` (s).

```Julia
julia> jovianyear(Metric) # s
au⁻³ᐟ²kG⁻¹2²³3¹⁷ᐟ²5¹⁴⋅1.321238687229(45) × 10⁸ = 3.74444292140(17) × 10⁸ [s] Metric

julia> jovianyear(MPH) # h
au⁻³ᐟ²kG⁻¹2¹⁹3¹³ᐟ²5¹²⋅1.321238687229(45) × 10⁸ = 104012.3033722(47) [h] MPH

julia> jovianyear(IAU) # D
au⁻³ᐟ²kG⁻¹2¹⁶3¹¹ᐟ²5¹²⋅1.321238687229(45) × 10⁸ = 4333.84597384(20) [D] IAU☉
```
