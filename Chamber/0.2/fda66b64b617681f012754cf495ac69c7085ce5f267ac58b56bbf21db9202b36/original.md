```
exsolve3(composition::Silicic, P::Float64, T::Float64, m_eq::Float64)::NamedTuple{(:C_co2, :X_co2), NTuple{2, Float64}}
```

Takes pressure, temperature, and amount of water to solve for the concentration of CO2 and X_CO2 using a Newton Raphson scheme

## Arguments

  * `composition`: `Silicic()`
  * `P`: pressure (Pa)
  * `T`: temperature (K)
  * `m_eq`: amount of water

## Returns

A NamedTuple with the following fields:

  * `C_co2`: The concentration of CO2 in the melt.
  * `X_co2`: The mole fraction of CO2 in the gas.
