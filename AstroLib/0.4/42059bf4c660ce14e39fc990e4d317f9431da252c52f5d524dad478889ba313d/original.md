```
geodetic2geo(latitude, longitude, altitude) -> latitude, longitude, altitude
geodetic2geo(latitude, longitude, altitude, planet) -> latitude, longitude, altitude
geodetic2geo(latitude, longitude, altitude, equatorial_radius, polar_radius) -> latitude, longitude, altitude
```

### Purpose

Convert from geodetic (or planetodetic) to geographic coordinates.

### Explanation

Converts from geodetic (latitude, longitude, altitude) to geographic (latitude, longitude, altitude).  In geographic coordinates, the Earth is assumed a perfect sphere with a radius equal to its equatorial radius.  The geodetic (or ellipsoidal) coordinate system takes into account the Earth's oblateness.

Geographic and geodetic longitudes are identical.  Geodetic latitude is the angle between local zenith and the equatorial plane.  Geographic and geodetic altitudes are both the closest distance between the satellite and the ground.

### Arguments

The function has two base methods.  The arguments common to all methods and always mandatory are `latitude`, `longitude`, and `altitude`:

  * `latitude`: geodetic latitude, in degrees.
  * `longitude`: geodetic longitude, in degrees.
  * `altitude`: geodetic altitude, in kilometers.

In order to convert to geographic coordinates, you can either provide custom equatorial and polar radii of the planet or use the values of one of the planets of Solar System (Pluto included).

If you want to use the method with explicit equatorial and polar radii the additional mandatory arguments are:

  * `equatorial_radius`: value of the equatorial radius of the body, in kilometers.
  * `polar_radius`: value of the polar radius of the body, in kilometers.

Instead, if you want to use the method with the selection of a planet, the only additional argument is the planet name:

  * `planet` (optional string argument): string with the name of the Solar System planet, from "Mercury" to "Pluto".  If omitted (so, when only `latitude`, `longitude`, and `altitude` are provided), the default is "Earth".

In all cases, the three coordinates can be passed as a 3-tuple `(latitude, longitude, altitude)`.  In addition, geodetic `latitude`, `longitude`, and `altitude` can be given as arrays of the same length.

### Output

The 3-tuple `(latitude, longitude, altitude)` in geographic coordinates, for the body with specified equatorial and polar radii (Earth by default).

If geodetic coordinates are given as arrays, a 3-tuple of arrays of the same length is returned.

### Method

Stephen P.  Keeler and Yves Nievergelt, "Computing geodetic coordinates", SIAM Rev. Vol. 40, No. 2, pp. 300-309, June 1998 (DOI:[10.1137/S0036144597323921](http://dx.doi.org/10.1137/S0036144597323921)).

Planetary constants from "Allen's Astrophysical Quantities", Fourth Ed., (2000).

### Example

Find geographic coordinates of geodetic North pole (latitude: 90°, longitude: 0°, altitude 0 km) of the Earth:

```jldoctest
julia> using AstroLib

julia> geodetic2geo(90, 0, 0)
(90.0, 0.0, -21.38499999999931)
```

The same for Jupiter:

```jldoctest
julia> using AstroLib

julia> geodetic2geo(90, 0, 0, "Jupiter")
(90.0, 0.0, -4638.0)
```

Find geographic coordinates for point of geodetic coordinates (latitude, longitude, altitude) = (43.16°, -24.32°, 3.87 km) on a planet with equatorial radius 8724.32 km and polar radius 8619.19 km:

```jldoctest
julia> using AstroLib

julia> geodetic2geo(43.16, -24.32, 3.87, 8724.32, 8619.19)
(42.46772711708433, -24.32, -44.52902080669082)
```

### Notes

`geo2geodetic` converts from geographic (or planetographic) to geodetic coordinates.

Code of this function is based on IDL Astronomy User's Library.
