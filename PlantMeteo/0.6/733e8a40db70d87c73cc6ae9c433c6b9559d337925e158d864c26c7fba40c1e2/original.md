```
air_density(Tₐ, P; check=true)
air_density(Tₐ, P, Rd, K₀; check=true)
```

ρ, the air density (kg m-3).

# Arguments

  * `Tₐ` (Celsius degree): air temperature
  * `P` (kPa): air pressure
  * `Rd` (J kg-1 K-1): gas constant of dry air (see Foken p. 245, or R bigleaf package).
  * `K₀` (Celsius degree): temperature in Celsius degree at 0 Kelvin
  * `check` (Bool): check if P is in the 85-110 kPa earth range

# Note

Rd and K₀ are Taken from [`Constants`](@ref) if not provided.

# References

Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany.
