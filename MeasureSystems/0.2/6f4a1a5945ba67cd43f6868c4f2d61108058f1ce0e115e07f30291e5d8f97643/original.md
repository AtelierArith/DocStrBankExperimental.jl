```Julia
second(U::UnitSystem) = time(𝟏,U,Metric)
time : [T], [T], [T], [T], [T]
T⋅(𝘤⋅R∞⋅α⁻²τ⋅2 = 7.7634407063(24) × 10²⁰) [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] Unified
```

Unit of `time` defined by `hyperfine` transition frequency of Cs-133 atom (s).

```Julia
julia> second(Metric) # s
𝟏 = 1.0 [s] Metric

julia> second(MPH) # h
2⁻⁴3⁻²5⁻² = 0.00027777777777777783 [h] MPH

julia> second(IAU) # D
2⁻⁷3⁻³5⁻² = 1.1574074074074075×10⁻⁵ [D] IAU☉
```
