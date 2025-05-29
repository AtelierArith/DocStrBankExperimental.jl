```
geo2mag(latitude, longitude[, year]) -> geomagnetic_latitude, geomagnetic_longitude
```

### Purpose

Convert from geographic to geomagnetic coordinates.

### Explanation

Converts from geographic (latitude, longitude) to geomagnetic (latitude, longitude).  Altitude is not involved in this function.

### Arguments

  * `latitude`: geographic latitude (North), in degrees.
  * `longitude`: geographic longitude (East), in degrees.
  * `year` (optional numerical argument): the year in which to perform conversion. If omitted, defaults to current year.

The coordinates can be passed as arrays of the same length.

### Output

The 2-tuple of magnetic (latitude, longitude) coordinates, in degrees.

If geographical coordinates are given as arrays, a 2-tuple of arrays of the same length is returned.

### Example

Kyoto has geographic coordinates 35° 00' 42'' N, 135° 46' 06'' E, find its geomagnetic coordinates in 2016:

```jldoctest
julia> using AstroLib

julia> geo2mag(ten(35,0,42), ten(135,46,6), 2016)
(36.86579228937769, -60.1840605366516)
```

### Notes

This function uses list of North Magnetic Pole positions provided by World Magnetic Model (https://www.ngdc.noaa.gov/geomag/data/poles/NP.xy).

`mag2geo` converts geomagnetical coordinates to geographic coordinates.

Code of this function is based on IDL Astronomy User's Library.
