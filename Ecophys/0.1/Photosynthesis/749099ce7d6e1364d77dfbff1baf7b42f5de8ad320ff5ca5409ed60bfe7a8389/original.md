```
gb(p::gbType, ws, Tleaf, Tair, P)
```

Compute boundary layer conductance for heat, water vapor and CO2.

# Arguments

  * `p`: Model of boundary layer conductance
  * `ws`: Wind speed (m/s)
  * `Tleaf`: Leaf temperature (K)
  * `Tair`: Air temperature (K)
  * `P`: Air pressure (Pa)

# Returns

  * `gbh`: Boundary layer conductance for heat (mol/m2/s)
  * `gbw`: Boundary layer conductance for water vapor (mol/m²/s)
  * `gbc`: Boundary layer conductance for CO2 (mol/m²/s)
