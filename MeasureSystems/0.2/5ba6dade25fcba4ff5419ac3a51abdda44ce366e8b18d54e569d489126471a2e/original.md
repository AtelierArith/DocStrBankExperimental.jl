```Julia
siderealyear(U::UnitSystem) = gaussianyear(U)/√(𝟏+earthmass(IAU)+lunarmass(IAU))
time : [T], [T], [T], [T], [T]
T/1.0000015202151904 ± 3.1e-15 [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] Unified
```

Orbit `time` defined by `gaussgravitation` constant `kG` and Earth-Moon system `mass` (s).

```Julia
julia> siderealyear(Metric) # s
kG⁻¹2¹⁴3⁷5⁵/1.0000015202151904(31) = 3.1558148013226100(98) × 10⁷ [s] Metric

julia> siderealyear(MPH) # h
kG⁻¹2¹⁰3⁵5³/1.0000015202151904(31) = 8766.152225896140(27) [h] MPH

julia> siderealyear(IAU) # D
kG⁻¹2⁷3⁴5³/1.0000015202151904(31) = 365.2563427456725(11) [D] IAU☉
```
