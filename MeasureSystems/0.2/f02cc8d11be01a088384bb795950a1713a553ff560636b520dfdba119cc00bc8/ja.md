```Julia
mass : [M], [FL⁻¹T²], [M], [M], [M]
mass(U::UnitSystem,S::UnitSystem) = electronmass(S)/electronmass(U)
mass(v::Real,U::UnitSystem,S::UnitSystem) = v/mass(U,S)
M [mₑ] 統一

慣性 `mass` または物質量または加速度に対する抵抗 (kg)、単位換算係数。

```

Julia julia> mass(CGS,Metric) # kg⋅g⁻¹ 2⁻³5⁻³ = 0.001 [kg]/[g] ガウス -> メトリック

julia> mass(CODATA,Metric) # kg⋅kg⁻¹ 𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [kg]/[kg] CODATA -> メトリック

julia> mass(Conventional,Metric) # kg⋅kg⁻¹ 𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [kg]/[kg] 従来 -> メトリック

julia> mass(English,Metric) # kg⋅slug⁻¹ lb = 0.45359237 [kg]/[lbm] 英語 -> メトリック

julia> mass(IAU,Metric) # kg⋅m⊙⁻¹ 𝘩⁻¹𝘤⁻¹au³kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1.988409(44) × 10³⁰ [kg]/[M☉] IAU☉ -> メトリック

julia> mass(PlanckGauss,Metric) # kg⋅mP⁻¹ mP = 2.176434(24) × 10⁻⁸ [kg]/[mP] プランクガウス -> メトリック ```
