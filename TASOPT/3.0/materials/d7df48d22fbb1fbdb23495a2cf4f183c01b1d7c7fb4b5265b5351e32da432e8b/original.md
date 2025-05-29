```julia
struct Conductor
```

Generic conductor.

  * `name::String`: Name
  * `ρ::Float64`: Density [kg/m³]
  * `resistivity::Float64`: Resistivity [Ω⋅m]
  * `α::Float64`: Thermal coefficient of resitivity [K⁻¹]
  * `T0::Float64`: Temperature at base resistivity [K]
