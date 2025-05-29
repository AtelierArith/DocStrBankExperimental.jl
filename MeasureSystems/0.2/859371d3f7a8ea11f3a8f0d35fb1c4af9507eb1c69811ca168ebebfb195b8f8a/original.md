```Julia
minute(U::UnitSystem) = 𝟐^2*𝟑*𝟓*second(U)
time : [T], [T], [T], [T], [T]
T⋅(𝘤⋅R∞⋅α⁻²τ⋅2³3⋅5 = 4.6580644238(14) × 10²²) [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] Unified
```

Unit of `time` defined by 60 `second` intervals (s).

```Julia
julia> minute(Metric) # s
2²3⋅5 = 60.0 [s] Metric

julia> minute(MPH) # h
2⁻²3⁻¹5⁻¹ = 0.016666666666666666 [h] MPH

julia> minute(IAU) # D
2⁻⁵3⁻²5⁻¹ = 0.0006944444444444445 [D] IAU☉
```
