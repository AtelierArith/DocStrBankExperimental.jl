```
dwater_dx(composition::Silicic, p::T, t::T, x::T)::T where {T<:Float64}
```

  * Function for the derivative of water with reference to X_CO2
  * This function is used within the `exsolve3` function.

## Arguments

  * `p`: pressure (Pa)
  * `t`: temperature (K)
  * `x`: The previous mole fraction of CO2 (X_CO2)
