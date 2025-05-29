```
eos_g(P::Float64, T::Float64)::EosG{Float64}
```

parametrization of redlich kwong taken from Huber et al. 2010

## Arguments

  * `P`: Pressure (Pa)
  * `T`: Temperature (K)

## Returns

An instance of the `EosG` struct, containing the following fields:

  * `rho_g`: density of the gas (kg/m³).
  * `drho_g_dP`: partial derivative of the density with respect to pressure (kg/m³/Pa).
  * `drho_g_dT`: partial derivative of the density with respect to temperature (kg/m³/K).
