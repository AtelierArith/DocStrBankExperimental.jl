```julia
struct ThermalInsulator
```

Generic thermal insulator.

  * `name::String`: Name
  * `ρ::Float64`: Density [kg/m³]
  * `conductivity_coeffs::Vector{Float64}`: Coefficients for thermal conductivity as a function of temperature [W/(m⋅K)]
