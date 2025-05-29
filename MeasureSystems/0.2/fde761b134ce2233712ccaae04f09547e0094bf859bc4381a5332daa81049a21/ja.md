```Julia
spectralexposure : [FL⁻¹T], [FL⁻¹T], [MT⁻¹], [MT⁻¹], [MT⁻¹]
spectralexposure(U::UnitSystem,S::UnitSystem) = force(U,S)/speed(U,S)
spectralexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/spectralexposure(U,S)
FL⁻¹T [ħ⁻¹𝘤²mₑ²ϕ⁻¹g₀⁻²] 統一

スペクトルエクスポージャーまたは `フルエンス` は `周波数` あたり (N⋅s⋅m⁻¹, J⋅s⋅m⁻²)、単位換算係数です。

```

Julia julia> spectralexposure(CGS,Metric) # kg⋅g⁻¹ 2⁻³5⁻³ = 0.001 [N⋅m⁻¹]/[dyn⋅cm⁻¹] ガウス -> メトリック

julia> spectralexposure(CGS,English) # lb⋅g⁻¹ g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] ガウス -> 英語

julia> spectralexposure(CODATA,Metric) # kg⋅kg⁻¹ 𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [N]/[N] CODATA -> メトリック

julia> spectralexposure(Conventional,Metric) # kg⋅kg⁻¹ 𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [N]/[N] 従来 -> メトリック

julia> spectralexposure(English,Metric) # kg⋅lb⁻¹ g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] 英語 -> メトリック ```
