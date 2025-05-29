```
clear_sky(;lat, DOY, t, altitude = 0.0, TL = 4.0)
```

Calculate global, direct and diffuse solar radiation on the horizontal plane using the clear sky model by Ineichen and Perez (2002).

# Arguments

  * `lat`: latitude in radians
  * `DOY`: day of year
  * `f`: fraction of the day (0 = sunrise, 1 = sunset)
  * `altitude`: altitude above sea level in meters (default 0.0)
  * `TL`: Linke turbidity coefficient (default 4.0)

# Returns

A named tuple with fields:

  * `Ig`: global solar radiation on the horizontal plane in W/m^2
  * `Idir`: direct solar radiation on the horizontal plane in W/m^2
  * `Idif`: diffuse solar radiation on the horizontal plane in W/m^2
  * `theta`: solar zenith angle in radians
  * `phi`: solar azimuth angle in radians

# References

Ineichen P., Perez R., A new airmass independent formulation for the Linke turbidity coefficient, Solar Energy, Vol 73(3), pp.151–157, 2002.
