```
calc_sun_position_MOD(JD::Number)
```

Compute the Sun position at the Julian Day `JD`.

Results are represented in the Mean Equinox of Date (MOD), i.e. accounting for precession but not for nutation and smaller perturbation of the polar axes, in spherical ecliptic and equatorial coordinates.  The algorithm was adapted from [Vallado 2013, p. 277-279].

# Arguments:

  * `JD`: time given as Julian Day .

# Value

`NamedTuple`: sun position where

  * Ecliptic coordinates (1:3)

      * λ: Ecliptic longitude of the Sun [rad].
      * β: Ecliptic latitude of the Sun [rad] is assumed 0.
      * r: Distance of the Sun from Earth [m].
  * Equatorial coordinate (4:5)  

      * α: ascention [rad]
      * δ: declination [rad]
  * ϵ: Obliquity of the ecliptic [rad].

# References

  * Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.      Microcosm Press, Hawthorne, CA.
