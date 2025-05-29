```
parameters_melting_curve(composition::Silicic, mH2O::Float64, mCO2::Float64, P::Float64)::NamedTuple{(:a, :dadx, :dady, :dadz, :b, :dbdx, :dbdy, :dbdz, :c, :dcdx, :dcdy, :dcdz), NTuple{12, Float64}}
```

  * This function is used within the `find_liq`, `crystal_fraction`, `crystal_fraction_eps_x` function.

## Arguments

  * `composition`: `Silicic()`
  * `mH2O`: Weight fration of the H2O in magma.
  * `mCO2`: Weight fration of the CO2 in magma.
  * `P`: Pressure (Pa)
