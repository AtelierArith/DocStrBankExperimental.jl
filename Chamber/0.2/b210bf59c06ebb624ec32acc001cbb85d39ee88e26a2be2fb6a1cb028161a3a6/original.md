```
water(composition::Silicic, p::T, t::T, x::T, c::T)::T where {T<:Float64}
```

  * Water Paritioning Function
  * This function is used within the `exsolve3` function.

## Arguments

  * `p`: pressure (Pa)
  * `t`: temperature (K)
  * `x`: The previous mole fraction of CO2 (X_CO2)
  * `c`: amount of water
