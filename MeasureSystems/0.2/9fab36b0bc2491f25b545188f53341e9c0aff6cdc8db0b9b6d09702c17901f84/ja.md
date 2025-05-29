```Julia
slug(U::UnitSystem) = mass(𝟏,U,British)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⋅ft⁻¹lb⋅2⁻¹ = 1.60207357768(49) × 10³¹) [mₑ] 統一

British gravitational `slug` 単位の `mass` (kg または lb).

```

Julia julia> slug(Metric) # kg g₀⋅ft⁻¹lb = 14.593902937206364 [kg] メトリック

julia> slug(CGS) # g g₀⋅ft⁻¹lb⋅2³5³ = 14593.902937206363 [g] ガウス

julia> slug(English) # lb g₀⋅ft⁻¹ = 32.17404855643044 [lbm] 英語

julia> slug(British) # slug 𝟏 = 1.0 [slug] ブリティッシュ

julia> slug(Gravitational) # hyl ft⁻¹lb = 1.4881639435695537 [hyl] 重力 ```
