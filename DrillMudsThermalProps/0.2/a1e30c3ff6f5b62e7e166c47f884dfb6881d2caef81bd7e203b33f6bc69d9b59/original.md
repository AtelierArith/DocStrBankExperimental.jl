```
TestFluid <: Fluid
```

Type defined as a template fluid with all the minimum parameters required to define new fluids in the package. For all properties, the function call with this fluid should trhow an error for not implemented property.

# Parameters

  * `name::Symbol`: Name of the Fluid. Default value: `:TestFluid`.
  * `ρ::Float64`: Density of the Fluid in the std condition in [kg/m³]. Default value: `1000.0`.
  * `cₚ::Float64`: Specific Heat of the Fluid in the std condition in [J/kg K]. Default value: `4000.0`.
  * `μ::Flaot64`: Dynamic viscosity of the Fluid in the std condition i [Pa s]. Default value: `1.002E-3`.
  * `k::Float64`: Thermal conductivity of the Fluid in the std condition in [W/m K]. Default value: `0.58`.
