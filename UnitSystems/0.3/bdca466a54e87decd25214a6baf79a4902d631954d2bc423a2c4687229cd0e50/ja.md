```Julia
mass(U::UnitSystem,S::UnitSystem) = electronmass(S)/electronmass(U)
mass(v::Real,U::UnitSystem,S::UnitSystem) = v/mass(U,S)
```

慣性 `mass` または物質量または加速度に対する抵抗 (kg)、単位変換係数。

```Julia
julia> mass(CGS,Metric) # kg⋅g⁻¹
0.001

julia> mass(CODATA,Metric) # kg⋅kg⁻¹
1.000000016738611

julia> mass(Conventional,Metric) # kg⋅kg⁻¹
1.000000195536555

julia> mass(English,Metric) # kg⋅slug⁻¹
0.45359237

julia> mass(IAU,Metric) # kg⋅m⊙⁻¹
1.9884092485076926e30

julia> mass(PlanckGauss,Metric) # kg⋅mP⁻¹
2.176434e-8
```
