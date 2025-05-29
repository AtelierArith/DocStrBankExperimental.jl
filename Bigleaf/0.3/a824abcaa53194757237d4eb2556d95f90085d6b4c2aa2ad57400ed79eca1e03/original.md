```
kinematic_viscosity(Tair,pressure; ...)
```

Calculate the kinematic viscosity of air.

# Parameters

  * Tair      Air temperature (deg C)
  * pressure  Atmospheric pressure (kPa)

optional 

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries    Kelvin, pressure0, Tair0, kPa2Pa

# Details

Eq where v is the kinematic viscosity of the air (m2 s-1),           given by (Massman 1999b):

$v = 1.327 * 10^-5(pressure0/pressure)(Tair/Tair0)^{1.81}$

# Value

kinematic viscosity of air (m2 s-1)

# References

Massman, W.J., 1999b: Molecular diffusivities of Hg vapor in air,              O2 and N2 near STP and the kinematic viscosity and thermal diffusivity             of air near STP. Atmospheric Environment 33, 453-457.      

# Examples

```jldoctest; output = false
Tair,pressure = 25.0,100.0
vis = kinematic_viscosity(Tair,pressure)
≈(vis, 1.58e-5, atol =1e-7)
# output
true
```
