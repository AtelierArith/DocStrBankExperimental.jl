```
eq2hor(ra, dec, jd[, obsname; ws=false, B1950=false, precession=true, nutate=true,
       aberration=true, refract=true, pressure=NaN, temperature=NaN]) -> alt, az, ha

eq2hor(ra, dec, jd, lat, lon[, altitude=0; ws=false, B1950=false,
       precession=true, nutate=true, aberration=true, refract=true,
       pressure=NaN, temperature=NaN]) -> alt, az, ha
```

### Purpose

Convert celestial  (ra-dec) coords to local horizon coords (alt-az).

### Explanation

This code calculates horizon (alt,az) coordinates from equatorial (ra,dec) coords. It performs precession, nutation, aberration, and refraction corrections.

### Arguments

This function has two base methods.  With one you can specify the name of the observatory, if present in `AstroLib.observatories`, with the other one you can provide the coordinates of the observing site and, optionally, the altitude.

Common mandatory arguments:

  * `ra`: right ascension of object, in degrees
  * `dec`: declination of object, in degrees
  * `jd`: julian date

Other positional arguments:

  * `obsname`: set this to a valid observatory name in `AstroLib.observatories`.

or

  * `lat`: north geodetic latitude of location, in degrees.
  * `lon`: AST longitude of location, in degrees. You can specify west longitude with a negative sign.
  * `altitude`: the altitude of the observing location, in meters.  It is `0` by default

Optional keyword arguments:

  * `ws` (optional boolean keyword): set this to `true` to get the azimuth measured westward from south (not East of North)
  * `B1950` (optional boolean keyword): set this to `true` if the ra and dec are specified in B1950 (FK4 coordinates) instead of J2000 (FK5). This is `false` by default
  * `precession` (optional boolean keyword): set this to `false` for no precession correction, `true` by default
  * `nutate` (optional boolean keyword): set this to `false` for no nutation, `true` by default
  * `aberration` (optional boolean keyword): set this to `false` for no aberration correction, `true` by default
  * `refract` (optional boolean keyword): set this to `false` for no refraction correction, `true` by default
  * `pressure` (optional keyword): the pressure at the observing location, in millibars. Default value is `NaN`
  * `temperature` (optional keyword): the temperature at the observing location, in Kelvins. Default value is `NaN`

### Output

  * `alt`: altitude of horizon coords, in degrees
  * `az`: azimuth angle measured East from North (unless ws is `true`), in degrees
  * `ha`: hour angle, in degrees

### Example

```jldoctest
julia> using AstroLib

julia> alt_o, az_o = eq2hor(ten(6,40,58.2)*15, ten(9,53,44), 2460107.25, ten(50,31,36),
                            ten(6,51,18), 369, pressure = 980, temperature=283)
(16.423991509721567, 265.60656932130564, 76.11502253130612)

julia> adstring(az_o, alt_o)
" 17 42 25.6  +16 25 26"
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
