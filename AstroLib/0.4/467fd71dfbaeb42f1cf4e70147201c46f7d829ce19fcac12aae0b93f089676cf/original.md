```
co_nutate(jd, ra, dec) -> d_ra, d_dec, eps, d_psi, d_eps
```

### Purpose

Calculate changes in RA and Dec due to nutation of the Earth's rotation

### Explanation

Calculates necessary changes to ra and dec due to the nutation of the Earth's rotation axis, as described in Meeus, Chap 23. Uses formulae from Astronomical Almanac, 1984, and does the calculations in equatorial rectangular coordinates to avoid singularities at the celestial poles.

### Arguments

  * `jd`: julian date, scalar or vector
  * `ra`: right ascension in degrees, scalar or vector
  * `dec`: declination in degrees, scalar or vector

### Output

The 5-tuple `(d_ra, d_dec, eps, d_psi, d_eps)`:

  * `d_ra`: correction to right ascension due to nutation, in degrees
  * `d_dec`: correction to declination due to nutation, in degrees
  * `eps`: the true obliquity of the ecliptic
  * `d_psi`: nutation in the longitude of the ecliptic
  * `d_eps`: nutation in the obliquity of the ecliptic

### Example

Example 23a in Meeus: On 2028 Nov 13.19 TD the mean position of Theta Persei is 2h 46m 11.331s 49d 20' 54.54''. Determine the shift in position due to the Earth's nutation.

```jldoctest
julia> using AstroLib

julia> jd = jdcnv(2028,11,13,4,56)
2.4620887055555554e6

julia> co_nutate(jd,ten(2,46,11.331) * 15,ten(49,20,54.54))
(0.004400660977140092, 0.00172668646508356, 0.40904016038217555, 14.859389427896472, 2.703809037235057)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.

The output of `d_ra` and `d_dec` in IDL AstroLib is in arcseconds, however it is in degrees here.

This function calls [`mean_obliquity`](@ref) and [`nutate`](@ref).
