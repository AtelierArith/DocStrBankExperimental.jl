```
hadec2altaz(ha, dec, lat[, ws=true]) -> alt, az
```

### Purpose

Convert Hour Angle and Declination to Horizon (Alt-Az) coordinates.

### Explanation

Can deal with the NCP singularity.  Intended mainly to be used by program `eq2hor`.

### Arguments

Input coordinates may be either a scalar or an array, of the same dimension.

  * `ha`: the local apparent hour angle, in degrees.  The hour angle is the time that right ascension of 0 hours crosses the local meridian.  It is unambiguously defined.
  * `dec`: the local apparent declination, in degrees.
  * `lat`: the local geodetic latitude, in degrees, scalar or array.
  * `ws` (optional boolean keyword): if true, the output azimuth is measured West from South.  The default is to measure azimuth East from North.

`ha` and `dec` can be given as a 2-tuple `(ha, dec)`.

### Output

2-tuple `(alt, az)`

  * `alt`: local apparent altitude, in degrees.
  * `az`: the local apparent azimuth, in degrees.

The output coordinates are always floating points and have the same type (scalar or array) as the input coordinates.

### Example

Arcturus is observed at an apparent hour angle of 336.6829 and a declination of 19.1825 while at the latitude of +43° 4' 42''.  What are the local altitude and azimuth of this object?

```jldoctest
julia> using AstroLib

julia> alt, az = hadec2altaz(336.6829, 19.1825, ten(43, 4, 42))
(59.08617155005685, 133.3080693440254)
```

### Notes

`altaz2hadec` converts Horizon (Alt-Az) coordinates to Hour Angle and Declination.

Code of this function is based on IDL Astronomy User's Library.
