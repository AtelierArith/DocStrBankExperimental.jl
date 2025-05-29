```Julia
fluence : [FL⁻¹], [FL⁻¹], [MT⁻²], [MT⁻²], [MT⁻²]
fluence(U::UnitSystem,S::UnitSystem) = energy(U,S)/area(U,S
fluence(v::Real,U::UnitSystem,S::UnitSystem) = v/fluence(U,S)
FL⁻¹ [ħ⁻²𝘤⁴mₑ³ϕ⁻²g₀⁻³] 統一

放射線露出または `力` あたりの `長さ` または剛性 (N⋅m⁻¹, J⋅m⁻²)、単位換算係数。

```

Julia julia> fluence(CGS,Metric) # kg⋅g⁻¹ 2⁻³5⁻³ = 0.001 [kg]/[g] ガウス -> メトリック

julia> fluence(CGS,English) # lb⋅g⁻¹ g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] ガウス -> 英語

julia> fluence(CODATA,Metric) # kg⋅kg⁻¹ 𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [kg]/[kg] CODATA -> メトリック

julia> fluence(Conventional,Metric) # kg⋅kg⁻¹ 𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [N]/[N] 従来型 -> メトリック

julia> fluence(English,Metric) # kg⋅lb⁻¹ g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] 英語 -> メトリック ```
