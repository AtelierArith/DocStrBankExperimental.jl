```
Gb_Thom(ustar; constants)
compute_Gb!(df, ::Thom1972)
```

Boundary Layer Conductance according to Thom 1972, an empirical formulation for the  for heat transfer based on a simple ustar (friction velocity) dependency.

# Arguments

  * `ustar`     : Friction velocity (m s-1)
  * `df`        : DataFrame with above variables
  * `constants=`[`BigleafConstants`](@ref)`()`

# Details

The empirical equation for Rb suggested by Thom 1972 is:

$Rb = 6.2 {u^*}^{-0.67}$

Gb (=1/Rb) for water vapor and heat are assumed to be equal in this package.

# Value

see [`compute_Gb!`](@ref)

# References

  * Thom, A., 1972: Momentum, mass and heat exchange of vegetation. Quarterly Journal of the Royal Meteorological Society 98, 124-134.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987: A preliminary multiple resistance routine for deriving dry deposition velocities from measured quantities. Water, Air, and Soil Pollution 36, 311-330.

```@example; output = false
using DataFrames
df = DataFrame(ustar = SA[0.1,missing,0.3])
compute_Gb!(df, Thom1972())
propertynames(df) == [:ustar, :Gb_h]
```
