```Julia
inertia : [FL⁻¹T²], [FL⁻¹T²], [M], [M], [M]
inertia(U::UnitSystem,S::UnitSystem) = mass(U,S)/gravity(U,S)
inertia(v::Real,U::UnitSystem,S::UnitSystem) = v/inertia(U,S)
FL⁻¹T² [mₑ⋅g₀⁻¹] Unified
```

Inertal `mass` or matter quantity or resistance to aceleration (kg), unit conversion factor.

```Julia
julia> inertia(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [N⋅m⁻¹]/[dyn⋅cm⁻¹] Gauss -> Metric

julia> inertia(CODATA,Metric) # kg⋅kg⁻¹
𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [N]/[N] CODATA -> Metric

julia> inertia(Conventional,Metric) # kg⋅kg⁻¹
𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [N]/[N] Conventional -> Metric

julia> inertia(English,Metric) # kg⋅slug⁻¹
g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] English -> Metric

julia> inertia(IAU,Metric) # kg⋅m⊙⁻¹
𝘩⁻¹𝘤⁻¹au³kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1.988409(44) × 10³⁰ [kg]/[M☉] IAU☉ -> Metric

julia> inertia(PlanckGauss,Metric) # kg⋅mP⁻¹
mP = 2.176434(24) × 10⁻⁸ [kg]/[mP] PlanckGauss -> Metric
```
