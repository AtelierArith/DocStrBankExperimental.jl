```
extraterrestrial_radiation(doy::Number; ...)
extraterrestrial_radiation(datetime::TimeType; ...)
```

Compute the extraterrestrial solar radiation with the eccentricity correction. Computation follows Lanini, 2010 (Master thesis, Bern University).

# Arguments

  * doy: integer with day of year (DoY) starting at 1

optional 

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries 

      * solar_constant
  * `year`=2030: year to create timestamps. Due to precession results slightly change across decades.
  * `FT=typeof(constants.solar_constant)`: Specif Float type of the return value

# Value

extraterrestrial radiation (W_m-2) of type `FT`.

# Examples

```jldoctest; output = false
ex_rad = extraterrestrial_radiation(1)
≈(ex_rad, 1414, atol = 1)
# output
true
```
