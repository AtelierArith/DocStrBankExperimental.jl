```
exsolve_meq(composition::Mafic, P::Float64, T::Float64, X_co2::Float64)::Float64
```

Spetialized version of `exsolve` that computes `meq` only.

## Arguments

  * `composition`: `Mafic()`
  * `P`: Pressure (Pa)
  * `T`: Temperature (K)
  * `X_co2`: mole fraction of CO2 in gas.

## Returns

  * `meq`: amount of water
