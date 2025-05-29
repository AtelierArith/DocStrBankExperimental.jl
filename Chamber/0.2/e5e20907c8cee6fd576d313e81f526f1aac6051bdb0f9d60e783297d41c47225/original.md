```
find_liq(composition::Silicic, water::Float64, co2::Float64, P::Float64, ini_eps_x::Float64)::Float64
```

Given the weight fractions of H2O and CO2 in magma, and the pressure, finds the temperature at which the magma will crystallize and reach the desired volume fraction of crystals. The function uses the parameters of the melting curve and an error function to estimate the liquidus temperature.

## Arguments

  * `composition`: `Silicic()`
  * `water`: Weight fration of the H2O in magma.
  * `co2`: Weight fration of the CO2 in magma.
  * `P`: Pressure (Pa)
  * `ini_eps_x`: The starting volumn fraction of crystal.

## Returns

  * `Tl`: the estimated liquidus temperature (K).
