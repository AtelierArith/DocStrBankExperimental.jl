```Julia
synodicmonth(U::UnitSystem) = 𝟏/(𝟏/siderealmonth(U)-𝟏/siderealyear(U))
time : [T], [T], [T], [T], [T]
T⋅29.487179323 ± 3.3e-8 [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] 統一

Orbit `time` defined by `siderealmonth` and `siderealyear` of Sun-Earth-Moon system (s).

```

Julia julia> synodicmonth(Metric) # s 2⁷3³5²⋅29.487179323(33) = 2.5476922935(28) × 10⁶ [s] Metric

julia> synodicmonth(MPH) # h 2³3⋅29.487179323(33) = 707.69230376(79) [h] MPH

julia> synodicmonth(IAU) # D 29.487179323(33) = 29.487179323(33) [D] IAU☉ ```
