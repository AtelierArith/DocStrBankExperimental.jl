```
eci2geo(x, y, z, jd) -> latitude, longitude, altitude
```

### Purpose

Convert Earth-centered inertial coordinates to geographic spherical coordinates.

### Explanation

Converts from ECI (Earth-Centered Inertial) (x, y, z) rectangular coordinates to geographic spherical coordinates (latitude, longitude, altitude).  Julian day is also needed as input.

ECI coordinates are in km from Earth center at the supplied time (True of Date). Geographic coordinates assume the Earth is a perfect sphere, with radius equal to its equatorial radius.

### Arguments

  * `x`: ECI x coordinate at `jd`, in kilometers.
  * `y`: ECI y coordinate at `jd`, in kilometers.
  * `z`: ECI z coordinate at `jd`, in kilometers.
  * `jd`: Julian days.

The three coordinates can be passed as a 3-tuple `(x, y, z)`.  In addition, `x`, `y`, `z`, and `jd` can be given as arrays of the same length.

### Output

The 3-tuple of geographical coordinate (latitude, longitude, altitude).

  * `latitude`: latitude, in degrees.
  * `longitude`: longitude, in degrees.
  * `altitude`: altitude, in kilometers.

If ECI coordinates are given as arrays, a 3-tuple of arrays of the same length is returned.

### Example

Obtain the geographic direction of the vernal point on 2015-06-30T14:03:12.857, in geographic coordinates, at altitude 600 km.  Note: equatorial radii of Solar System planets in meters are stored into `AstroLib.planets` dictionary.

```jldoctest
julia> using AstroLib

julia> x = AstroLib.planets["earth"].eqradius*1e-3 + 600;

julia> lat, long, alt = eci2geo(x, 0, 0, jdcnv("2015-06-30T14:03:12.857"))
(0.0, 230.87301833205856, 600.0)
```

These coordinates can be further transformed into geodetic coordinates using `geo2geodetic` or into geomagnetic coordinates using `geo2mag`.

### Notes

`geo2eci` converts geographic spherical coordinates to Earth-centered inertial coordinates.

Code of this function is based on IDL Astronomy User's Library.
