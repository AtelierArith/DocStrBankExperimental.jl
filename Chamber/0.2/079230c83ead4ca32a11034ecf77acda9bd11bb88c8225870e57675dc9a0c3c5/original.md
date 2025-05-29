```
IC_Finder(composition::Silicic, M_h2o::Float64, M_co2::Float64, M_tot::Float64, P::Float64, T::Float64, V::Float64, rho_m::Float64, param_IC::ParamICFinder{Float64})::NamedTuple{(:eps_g0, :X_co20, :mco2_diss, :phase),NTuple{4,Float64}}
```

An iterative function that uses thermodynamic modeling to determine the gas phase composition of a silicic magma chamber.

## Arguments

  * `composition`: `Silicic()`
  * `M_h2o`: total mass of water in magma (kg)
  * `M_co2`: total mass of CO2 in magma (kg)
  * `M_tot`: total mass of magma (kg)
  * `P`: Pressure (Pa)
  * `T`: Temperature (K)
  * `V`: chamber volume (m³)
  * `rho_m`: density of the melt (kg/m³)
  * `param_IC`: An instance of the `ParamICFinder` composite type containing the parameters for IC_Finder

## Returns

A NamedTuple with the following fields:

  * `eps_g0`: Initial gas fraction of the magma chamber
  * `X_co20`: Initial mole fraction of CO2 in the gas phase
  * `mco2_diss`: Total mass of CO2 dissolved in the melt (kg)
  * `phase`: Integer representing the state of the magma

## Details

The function uses a thermodynamic model to find the initial gas fraction (`eps_g0`) and initial mole fraction of CO2 in the gas phase (`X_co20`) for a silicic magma chamber. The model assumes that the chamber contains two phases: a liquid melt and a gas phase. The model calculates the saturation state of the magma with respect to CO2, and determines whether the gas phase contains only CO2 or a mixture of CO2 and H2O. If the chamber is in two-phase state, the model returns `eps_g0 = 0.0`, `X_co20 = 0.0`, `mco2_diss = Total mass of CO2 dissolved in the melt`, and `phase = 2`. If the chamber is in gas or liquid state, the function iteratively solves for `eps_g0` and `X_co20` using the `solve_X_co2` and `get_eps_g` helper functions until the relative difference between `eps_g0` and `X_co20` in two consecutive iterations is less than the tolerance `Tol`, or until the maximum number of iterations `max_count` is reached. 
