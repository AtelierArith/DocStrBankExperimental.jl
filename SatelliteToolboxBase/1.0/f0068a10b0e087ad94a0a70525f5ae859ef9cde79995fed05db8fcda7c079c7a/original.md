```
Ellipsoid{T <: Number}
```

Ellipsoid of rotation to be used for geocentric, geodetic and ECEF transformations.

# Fields

  * `a::T` : Semi-major axis [m].
  * `f::T`: Flattening of the ellipsoid.
  * `b::T`: Semi-minor axis [m].
  * `e²::T`: Eccentricity squared.
  * `el²::T`: Second Eccentricity squared.
