```
exsolve(composition::Silicic, P::Float64, T::Float64, X_co2::Float64)::NamedTuple{(:meq, :dmeqdP, :dmeqdT, :dmeqdXco2, :C_co2, :dC_co2dP, :dC_co2dT, :dC_co2dXco2), NTuple{8, Float64}}
```

This script uses Liu et al. (2006) to calculate the solubility of water

## Arguments

  * `composition`: `Silicic()`
  * `P`: Pressure (Pa)
  * `T`: Temperature (K)
  * `X_co2`: mole fraction of CO2 in gas.
