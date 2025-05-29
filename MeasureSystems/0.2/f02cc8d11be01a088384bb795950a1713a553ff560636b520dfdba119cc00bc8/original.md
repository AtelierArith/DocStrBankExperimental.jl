```Julia
mass : [M], [FL⁻¹T²], [M], [M], [M]
mass(U::UnitSystem,S::UnitSystem) = electronmass(S)/electronmass(U)
mass(v::Real,U::UnitSystem,S::UnitSystem) = v/mass(U,S)
M [mₑ] Unified
```

Inertal `mass` or matter quantity or resistance to aceleration (kg), unit conversion factor.

```Julia
julia> mass(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [kg]/[g] Gauss -> Metric

julia> mass(CODATA,Metric) # kg⋅kg⁻¹
𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [kg]/[kg] CODATA -> Metric

julia> mass(Conventional,Metric) # kg⋅kg⁻¹
𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [kg]/[kg] Conventional -> Metric

julia> mass(English,Metric) # kg⋅slug⁻¹
lb = 0.45359237 [kg]/[lbm] English -> Metric

julia> mass(IAU,Metric) # kg⋅m⊙⁻¹
𝘩⁻¹𝘤⁻¹au³kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1.988409(44) × 10³⁰ [kg]/[M☉] IAU☉ -> Metric

julia> mass(PlanckGauss,Metric) # kg⋅mP⁻¹
mP = 2.176434(24) × 10⁻⁸ [kg]/[mP] PlanckGauss -> Metric
```
