```
air_density(Tair,pressure; ...)
```

Air density of moist air from air temperature and pressure_

# Arguments

  * Tair:      Air temperature (deg C)
  * pressure:  Atmospheric pressure (kPa)

optional 

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries   Kelvin, kPa2Pa

# Details

Air density $\rho$ is calculated as:

$\rho = {pressure \over Rd * Tair}$

# Value

air density (kg m-3)

# Examples

```@example doc
# air density at 25degC and standard pressure (101.325kPa)
air_density(25,101.325)
```

# References

Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany.
