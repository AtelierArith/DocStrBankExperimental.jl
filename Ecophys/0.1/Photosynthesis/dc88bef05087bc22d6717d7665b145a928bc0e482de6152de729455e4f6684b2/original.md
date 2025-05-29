```
transpiration(;gsw = 0.1, gbw = 1.0, Tleaf = 300.0, Tair = 298.0, P = 101e3,
               RH = 0.75)
```

Compute transpiration rate (mol/m^2/s) from conductance to water vapor and environmental variables.

# Arguments

  * `gsw`: Stomatal conductance to water vapor (mol/m^2/s)
  * `gbw`: Boundary layer conductance to water vapor (mol/m^2/s)
  * `Tleaf`: Leaf temperature (K)
  * `Tair`: Air temperature (K)
  * `P`: Air pressure (Pa)
  * `RH`: Relative humidity
