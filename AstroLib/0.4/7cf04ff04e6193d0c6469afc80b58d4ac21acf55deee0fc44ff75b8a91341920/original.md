```
gcirc(units, ra1, dec1, ra2, dec2) -> angular_distance
```

### Purpose

Computes rigorous great circle arc distances.

### Explanation

Input position can be either radians, sexagesimal right ascension and declination, or degrees.

### Arguments

  * `units`: integer, can be either 0, or 1, or 2.  Describes units of inputs and output:

      * 0: everything (input right ascensions and declinations, and output distance) is radians
      * 1: right ascensions are in decimal hours, declinations in decimal degrees, output distance in arc seconds
      * 2: right ascensions and declinations are in degrees, output distance in arc seconds
  * `ra1`:  right ascension or longitude of point 1
  * `dec1`: declination or latitude of point 1
  * `ra2`: right ascension or longitude of point 2
  * `dec2`: declination or latitude of point 2

Both `ra1` and `dec1`, and `ra2` and `dec2` can be given as 2-tuples `(ra1, dec1)` and `(ra2, dec2)`.

### Output

Angular distance on the sky between points 1 and 2, as a `AbstractFloat`.  See `units` argument above for the units.

### Method

"Haversine formula" see http://en.wikipedia.org/wiki/Great-circle_distance.

### Example

```jldoctest
julia> using AstroLib

julia> gcirc(0, 120, -43, 175, +22)
1.590442261600714
```

### Notes

  * The function `sphdist` provides an alternate method of computing a spherical distance.
  * The Haversine formula can give rounding errors for antipodal points.

Code of this function is based on IDL Astronomy User's Library.
