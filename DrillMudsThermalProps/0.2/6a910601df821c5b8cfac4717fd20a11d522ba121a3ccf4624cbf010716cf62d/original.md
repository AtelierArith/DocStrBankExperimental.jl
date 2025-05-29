```
TestSolid <: Solid
```

Type defined as a template solid with all the minimum parameters required to define new solids in the package. For all properties, the function call with this solid should trhow an error for not implemented property.

# Parameters

  * `name::Symbol`: Name of the Solid. Default value: `:TestSolid`.
  * `ρ::Float64`: Density of the Solid in the std condition in [kg/m³]. Default value: `1000.0`.
  * `cₚ::Float64`: Specific Heat of the Solid in the std condition in [J/kg K]. Default value: `4000.0`.
  * `k::Float64`: Thermal conductivity of the Solid in the std condition in [W/m K]. Default value: `0.58`.
