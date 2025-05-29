```Julia
inertia(U::UnitSystem,S::UnitSystem) = mass(U,S)/gravity(U,S)
inertia(v::Real,U::UnitSystem,S::UnitSystem) = v/inertia(U,S)
```

Inertal `mass` or matter quantity or resistance to aceleration (kg), unit conversion factor.

```Julia
julia> inertia(CGS,Metric) # kg⋅g⁻¹
0.001

julia> inertia(CODATA,Metric) # kg⋅kg⁻¹
1.000000016738611

julia> inertia(Conventional,Metric) # kg⋅kg⁻¹
1.000000195536555

julia> inertia(English,Metric) # kg⋅slug⁻¹
14.593902937206364

julia> inertia(IAU,Metric) # kg⋅m⊙⁻¹
1.9884092485076926e30

julia> inertia(PlanckGauss,Metric) # kg⋅mP⁻¹
2.176434e-8
```
