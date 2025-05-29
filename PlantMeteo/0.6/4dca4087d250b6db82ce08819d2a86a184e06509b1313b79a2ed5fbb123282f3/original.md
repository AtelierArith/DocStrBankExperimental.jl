```
vapor_pressure(Tₐ, Rh; check=true)
```

Vapor pressure (kPa) at given temperature (°C) and relative hunidity (0-1).

# Arguments

  * `Tₐ` (Celsius degree): air temperature
  * `Rh` (0-1): relative humidity
  * `check` (Bool): if true, check that `Rh` is between 0 and 1

# Examples

```julia
vapor_pressure(25.0, 0.4)
```
