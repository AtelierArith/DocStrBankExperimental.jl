```
compute_Gb_quantities(Gb_h)
compute_Gb_quantities!(df:::AbstractDataFrame)
```

Based on boundary layer conductance for heat, compute derived quantities.

# Arguments

  * `Gb_h` : Boundary layer conductance for heat transfer (m s-1)
  * `df`   : DataFrame with above columns
  * `constants=`[`BigleafConstants`](@ref)`()`: entries `Sc_CO2` and `Pr`

# Value

NamedTuple with entries

  * `Gb_h`: Boundary layer conductance for heat transfer (m s-1)
  * `Rb_h`: Boundary layer resistance for heat transfer (s m-1)
  * `kB_h`: kB^(-1) parameter for heat transfer
  * `Gb_CO2`: Boundary layer conductance for CO2 (m s-1).
