```
Gb_constant_kB1(ustar, kB_h; constants)
compute_Gb!(df, ::ConstantKB1})
```

Boundary Layer Conductance using constant kB^(-1) value for heat transfer.

# Arguments

  * `ustar`     : Friction velocity (m s-1)
  * `df`        : DataFrame with above variables
  * `kB_h`      : kB^(-1) value for heat transfer
  * `constants=`[`BigleafConstants`](@ref)`()`

# Details

Rb*h computed by ``kB*h/(k * ustar)``, where k is the von Karman constant.
