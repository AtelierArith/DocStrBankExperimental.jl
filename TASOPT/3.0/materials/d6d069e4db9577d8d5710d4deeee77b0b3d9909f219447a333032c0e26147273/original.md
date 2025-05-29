```julia
mutable struct StructuralAlloy
```

Generic structural alloy.

  * `name::String`: Name
  * `ρ::Float64`: Density [kg/m³]
  * `E::Float64`: Young's Modulus [Pa]
  * `G::Float64`: Shear Modulus [Pa]
  * `ν::Float64`: Poisson's Ratio [-]
  * `σmax::Float64`: Maximum Stress (Yield or Ultimate Strength) [Pa]
  * `τmax::Float64`: Maximum Shear [Pa]
  * `YTS::Float64`: Yield tensile strength [Pa]
  * `UTS::Float64`: Ultimate tensile strength [Pa]
  * `USS::Float64`: Ultimate shear strength [Pa]
  * `k::Float64`: Thermal conductivity [W/(m K)]
