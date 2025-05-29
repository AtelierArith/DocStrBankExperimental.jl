```
co_aberration(jd, ra, dec[, eps=NaN]) -> d_ra, d_dec
```

### Purpose

Calculate changes to right ascension and declination due to the effect of annual aberration

### Explanation

With reference to Meeus, Chapter 23

### Arguments

  * `jd`: julian date, scalar or vector
  * `ra`: right ascension in degrees, scalar or vector
  * `dec`: declination in degrees, scalar or vector
  * `eps` (optional): true obliquity of the ecliptic (in radians). It will be calculated if no argument is specified.

### Output

The 2-tuple `(d_ra, d_dec)`:

  * `d_ra`: correction to right ascension due to aberration, in arc seconds
  * `d_dec`: correction to declination due to aberration, in arc seconds

### Example

Compute the change in RA and Dec of Theta Persei (RA = 2h46m,11.331s, Dec = 49d20',54.5'') due to aberration on 2028 Nov 13.19 TD

```jldoctest
julia> using AstroLib

julia> jd = jdcnv(2028,11,13,4, 56)
2.4620887055555554e6

julia> co_aberration(jd,ten(2,46,11.331)*15,ten(49,20,54.54))
(30.04404628365077, 6.699400463119431)
```

d_ra = 30.04404628365103'' (≈ 2.003s)

d_dec = 6.699400463118504''

### Notes

Code of this function is based on IDL Astronomy User's Library.

The output d*ra is *not* multiplied by cos(dec), so that apparent*ra = ra + d_ra/3600.

These formula are from Meeus, Chapters 23.  Accuracy is much better than 1 arcsecond. The maximum deviation due to annual aberration is 20.49'' and occurs when the Earth's velocity is perpendicular to the direction of the star.

This function calls [`true_obliquity`](@ref) and [`sunpos`](@ref).
