```
mag2geo(latitude, longitude[, year]) -> geographic_latitude, geographic_longitude
```

### Purpose

Convert from geomagnetic to geographic coordinates.

### Explanation

Converts from geomagnetic (latitude, longitude) to geographic (latitude, longitude).  Altitude is not involved in this function.

### Arguments

  * `latitude`: geomagnetic latitude (North), in degrees.
  * `longitude`: geomagnetic longitude (East), in degrees.
  * `year` (optional numerical argument): the year in which to perform conversion. If omitted, defaults to current year.

The coordinates can be passed as arrays of the same length.

### Output

The 2-tuple of geographic (latitude, longitude) coordinates, in degrees.

If geomagnetic coordinates are given as arrays, a 2-tuple of arrays of the same length is returned.

### Example

Find position of North Magnetic Pole in 2016

```jldoctest
julia> using AstroLib

julia> mag2geo(90, 0, 2016)
(86.395, -166.29000000000002)
```

### Notes

This function uses list of North Magnetic Pole positions provided by World Magnetic Model (https://www.ngdc.noaa.gov/geomag/data/poles/NP.xy).

`geo2mag` converts geographic coordinates to geomagnetic coordinates.

Code of this function is based on IDL Astronomy User's Library.
