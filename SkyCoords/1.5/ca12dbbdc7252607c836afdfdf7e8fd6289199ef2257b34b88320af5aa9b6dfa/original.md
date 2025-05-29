```
ICRSCoords(ra, dec)
```

[International Celestial Reference System](https://en.wikipedia.org/wiki/International_Celestial_Reference_System)

This is the current standard adopted by the International Astronomical Union notably due to its high level of accuracy compared to standard equatorial coordinate systems. What sets this apart from [`FK5Coords`](@ref) is that it is completely defined using extragalactic radio sources rather than a geocentric frame, which means the reference frame will not change due to Earth's motion.

# Coordinates

  * `ra` - Right ascension in radians (0, 2π)
  * `dec` - Declination in radians (-π/2, π/2)
