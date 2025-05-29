```
posang(units, ra1, dec1, ra2, dec2) -> angular_distance
```

### Purpose

Compute rigorous position angle of point 2 relative to point 1.

### Explanation

Computes the rigorous position angle of point 2 (with given right ascension and declination) using point 1 (with given right ascension and declination) as the center.

### Arguments

  * `units`: integer, can be either 0, or 1, or 2.  Describes units of inputs and output:

      * 0: everything (input right ascensions and declinations, and output distance) is radians
      * 1: right ascensions are in decimal hours, declinations in decimal degrees, output distance in degrees
      * 2: right ascensions and declinations are in degrees, output distance in degrees
  * `ra1`:  right ascension or longitude of point 1
  * `dec1`: declination or latitude of point 1
  * `ra2`: right ascension or longitude of point 2
  * `dec2`: declination or latitude of point 2

Both `ra1` and `dec1`, and `ra2` and `dec2` can be given as 2-tuples `(ra1, dec1)` and `(ra2, dec2)`.

### Output

Angle of the great circle containing `[ra2, dec2]` from the meridian containing `[ra1, dec1]`, in the sense north through east rotating about `[ra1, dec1]`. See `units` argument above for units.

### Method

The "four-parts formula" from spherical trigonometry (p. 12 of Smart's Spherical Astronomy or p. 12 of Green' Spherical Astronomy).

### Example

Mizar has coordinates (ra, dec) = (13h 23m 55.5s, +54° 55' 31'').  Its companion, Alcor, has coordinates (ra, dec) = (13h 25m 13.5s, +54° 59' 17''). Find the position angle of Alcor with respect to Mizar.

```jldoctest
julia> using AstroLib

julia> posang(1, ten(13, 25, 13.5), ten(54, 59, 17), ten(13, 23, 55.5), ten(54, 55, 31))
-108.46011246802047
```

### Notes

  * The function `sphdist` provides an alternate method of computing a spherical

distance.

  * Note that `posang` is not commutative: the position angle between A and B is $θ$, then the position angle between B and A is $180 + θ$.

Code of this function is based on IDL Astronomy User's Library.
