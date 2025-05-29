```
dwater_dx(composition::Mafic, p::T, t::T, x::T)::T where {T<:Float64}
```

  * Derivative of Water Partitioning Function with respect to X_CO2
  * This function is used within the `exsolve3` function.

## Arguments

  * `p`: pressure (Pa)
  * `t`: temperature (K)
  * `x`: The previous mole fraction of CO2 (X_CO2)
