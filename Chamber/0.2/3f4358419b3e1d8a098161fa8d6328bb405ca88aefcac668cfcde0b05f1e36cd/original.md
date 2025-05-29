```
crystal_fraction(composition::Mafic, T::Float64, P::Float64, mH2O::Float64, mCO2::Float64)::NamedTuple{(:eps_x, :deps_x_dP, :deps_x_dT, :deps_x_deps_g, :deps_x_dmco2_t, :deps_x_dmh2o_t), NTuple{6, Float64}}
```

Calculate crystal volume fraction and its derivatives in magma at given temperature, pressure, and water and CO2 contents.

## Arguments

  * `composition`: `Mafic()`
  * `T`: Temperature (K)
  * `P`: Pressure (Pa)
  * `mH2O`: Weight fration of the H2O in magma.
  * `mCO2`: Weight fration of the CO2 in magma.

## Returns

A NamedTuple with the following fields:

  * `eps_x`: Crystal volume fraction.
  * `deps_x_dP`: Derivative of eps_x with respect to pressure.
  * `deps_x_dT`: Derivative of eps_x with respect to temperature.
  * `deps_x_deps_g`: Derivative of eps_x with respect to gas volume fraction.
  * `deps_x_dmco2_t`: Derivative of eps_x with respect to CO2 content.
  * `deps_x_dmh2o_t`: Derivative of eps_x with respect to H2O content.
