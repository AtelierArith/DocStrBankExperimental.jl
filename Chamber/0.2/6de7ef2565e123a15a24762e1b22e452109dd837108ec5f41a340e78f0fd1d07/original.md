```
boundary_conditions_new(P::Float64, T::Float64, V::Float64, rho_m::Float64, rho_x::Float64, c::Float64, sw::SW{Int8}, T_in::Float64, M_h2o::Float64, M_co2::Float64, total_Mass::Float64, param::Param{Float64}, param_saved_var::ParamSaved{Float64})
```

## Arguments

  * `P`: Pressure (Pa)
  * `T`: Temperature (K)
  * `V`: chamber volume (m³)
  * `rho_m`: density of melt
  * `rho_x`: density of crystal of magma
  * `c`: heat of magma
  * `sw`: eruption/cooling*module/viscous*relaxation control
  * `T_in`: Temperature
  * `M_h2o`: total mess of H2O in the magma
  * `M_co2`: total mess of CO2 in the magma
  * `total_Mass`: total mess of magma chamber
