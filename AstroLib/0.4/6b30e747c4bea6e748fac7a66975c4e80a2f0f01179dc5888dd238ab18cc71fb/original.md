```
geo2geodetic(latitude, longitude, altitude) -> latitude, longitude, altitude
geo2geodetic(latitude, longitude, altitude, planet) -> latitude, longitude, altitude
geo2geodetic(latitude, longitude, altitude, equatorial_radius, polar_radius) -> latitude, longitude, altitude
```

### Purpose

Convert from geographic (or planetographic) to geodetic coordinates.

### Explanation

Converts from geographic (latitude, longitude, altitude) to geodetic (latitude, longitude, altitude).  In geographic coordinates, the Earth is assumed a perfect sphere with a radius equal to its equatorial radius.  The geodetic (or ellipsoidal) coordinate system takes into account the Earth's oblateness.

Geographic and geodetic longitudes are identical.  Geodetic latitude is the angle between local zenith and the equatorial plane.  Geographic and geodetic altitudes are both the closest distance between the satellite and the ground.

### Arguments

The function has two base methods.  The arguments common to all methods and always mandatory are `latitude`, `longitude`, and `altitude`:

  * `latitude`: geographic latitude, in degrees.
  * `longitude`: geographic longitude, in degrees.
  * `altitude`: geographic altitude, in kilometers.

In order to convert to geodetic coordinates, you can either provide custom equatorial and polar radii of the planet or use the values of one of the planets of Solar System (Pluto included).

If you want to use the method with explicit equatorial and polar radii the additional mandatory arguments are:

  * `equatorial_radius`: value of the equatorial radius of the body, in kilometers.
  * `polar_radius`: value of the polar radius of the body, in kilometers.

Instead, if you want to use the method with the selection of a planet, the only additional argument is the planet name:

  * `planet` (optional string argument): string with the name of the Solar System planet, from "Mercury" to "Pluto".  If omitted (so, when only `latitude`, `longitude`, and `altitude` are provided), the default is "Earth".

In all cases, the three coordinates can be passed as a 3-tuple `(latitude, longitude, altitude)`.  In addition, geographical `latitude`, `longitude`, and `altitude` can be given as arrays of the same length.

### Output

The 3-tuple `(latitude, longitude, altitude)` in geodetic coordinates, for the body with specified equatorial and polar radii (Earth by default).

If geographical coordinates are given as arrays, a 3-tuple of arrays of the same length is returned.

### Method

Stephen P.  Keeler and Yves Nievergelt, "Computing geodetic coordinates", SIAM Rev. Vol. 40, No. 2, pp. 300-309, June 1998 (DOI:[10.1137/S0036144597323921](http://dx.doi.org/10.1137/S0036144597323921)).

Planetary constants are from Planetary Fact Sheet (http://nssdc.gsfc.nasa.gov/planetary/factsheet/index.html).

### Example

Locate the Earth geographic North pole (latitude: 90°, longitude: 0°, altitude 0 km), in geodetic coordinates:

```jldoctest
julia> using AstroLib

julia> geo2geodetic(90, 0, 0)
(90.0, 0.0, 21.38499999999931)
```

The same for Jupiter:

```jldoctest
julia> using AstroLib

julia> geo2geodetic(90, 0, 0, "Jupiter")
(90.0, 0.0, 4638.0)
```

Find geodetic coordinates for point of geographic coordinates (latitude, longitude, altitude) = (43.16°, -24.32°, 3.87 km) on a planet with equatorial radius 8724.32 km and polar radius 8619.19 km:

```jldoctest
julia> using AstroLib

julia> geo2geodetic(43.16, -24.32, 3.87, 8724.32, 8619.19)
(43.849399515234516, -24.32, 53.53354478670965)
```

### Notes

Whereas the conversion from geodetic to geographic coordinates is given by an exact, analytical formula, the conversion from geographic to geodetic isn't. Approximative iterations (as used here) exist, but tend to become less good with increasing eccentricity and altitude.  The formula used in this routine should give correct results within six digits for all spatial locations, for an ellipsoid (planet) with an eccentricity similar to or less than Earth's.  More accurate results can be obtained via calculus, needing a non-determined amount of iterations.

In any case, the function `geodetic2geo`, which converts from geodetic (or planetodetic) to geographic coordinates, can be used to estimate the accuracy of `geo2geodetic`.

```jldoctest
julia> using AstroLib

julia> collect(geodetic2geo(geo2geodetic(67.2, 13.4, 1.2))) - [67.2, 13.4, 1.2]
3-element Vector{Float64}:
 -3.5672513831741526e-9
  0.0
  9.484211194177306e-10
```

Code of this function is based on IDL Astronomy User's Library.
