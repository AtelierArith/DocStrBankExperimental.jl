```
Reynolds_Number(Tair,pressure,ustar,z0m; constants)
```

calculates the Roughness Reynolds Number.

# Arguments

  * `Tair`      : Air temperature (deg C)
  * `pressure`  : Atmospheric pressure (kPa)
  * `ustar`     : Friction velocity (m s-1)
  * `z0m`       : Roughness length (m)

optional

  * `constants=`[`BigleafConstants`](@ref)`()`

# Details

The Roughness Reynolds Number is calculated as in Massman 1999a:      $Re = z0m * ustar / v$, where `v` is the kinematic viscosity (m2 s-1).

# Value

Roughness Reynolds Number (-)

# References

Massman, W_J., 1999a: A model study of kB H- 1 for vegetated surfaces using 'localized near-field' Lagrangian theory. Journal of Hydrology 223, 27-43.

```jldoctest; output = false
Tair,pressure,ustar,z0m = 25.0,100.0,0.5,0.5
R = Reynolds_Number(Tair,pressure,ustar,z0m)                             
≈(R, 15870, rtol=1e-3) 
# output
true
```
