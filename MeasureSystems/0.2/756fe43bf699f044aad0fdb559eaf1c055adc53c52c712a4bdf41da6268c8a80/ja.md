```Julia
boiling(U::UnitSystem) = temperature(T₀+Constant(99.9839),U)
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
Θ⋅373.1339 [kB⁻¹𝘤²mₑ⋅g₀⁻¹] 統一

水の沸点における標準 `temperature` 参照 (K または °R)。

```

Julia julia> boiling(Metric) # K 373.1339 = 373.1339 [K] メトリック

julia> boiling(SI2019) # K NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³⋅373.1339 = 373.13389987(11) [K] SI2019

julia> boiling(English) # °R 3²5⁻¹⋅373.1339 = 671.64102 [°R] 英語 ```
