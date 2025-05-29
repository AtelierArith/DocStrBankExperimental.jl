```
props = calculate_properties(fluid, T, P, verbose=true)
```

Use equation of state to calculate density, fugacity, and molar volume of a real fluid at a given temperature and pressure.

# Arguments

  * `fluid::Union{PengRobinsonFluid, VdWFluid}`: Peng-Robinson/ van der Waals fluid data structure
  * `T::Float64`: Temperature (units: Kelvin)
  * `P::Float64`: Pressure (units: bar)
  * `verbose::Bool`: will print results if `true`

# Returns

  * `prop_dict::Dict`: Dictionary of Peng-Robinson/ van der Waals fluid properties
