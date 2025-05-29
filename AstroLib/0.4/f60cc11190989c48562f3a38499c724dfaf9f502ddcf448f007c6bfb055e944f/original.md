```
gal_uvw(ra, dec, pmra, pmdec, vrad, plx[, lsr=true]) -> u, v, w
```

### Purpose

Calculate the Galactic space velocity $(u, v, w)$ of a star.

### Explanation

Calculates the Galactic space velocity $(u, v, w)$ of a star given its (1) coordinates, (2) proper motion, (3) parallax, and (4) radial velocity.

### Arguments

User must supply a position, proper motion, radial velocity and parallax. Either scalars or arrays all of the same length can be supplied.

1. Position:

      * `ra`: right ascension, in degrees
      * `dec`: declination, in degrees
2. Proper Motion

      * `pmra`: proper motion in right ascension in arc units (typically milli-arcseconds/yr).  If given $μ_α$ – proper motion in seconds of time/year – then this is equal to $15 μ_α \cos(\text{dec})$.
      * `pmdec`: proper motion in declination (typically mas/yr).
3. Radial Velocity

      * `vrad`: velocity in km/s
4. Parallax

      * `plx`: parallax with same distance units as proper motion measurements typically milliarcseconds (mas)

If you know the distance in parsecs, then set `plx` to $1000/\text{distance}$, if proper motion measurements are given in milli-arcseconds/yr.

There is an additional optional keyword:

  * `lsr` (optional boolean keyword): if this keyword is set to `true`, then the output velocities will be corrected for the solar motion $(u, v, w)_⊙ = (-8.5, 13.38, 6.49)$ (Coşkunoǧlu et al. 2011 MNRAS, 412, 1237; DOI:[10.1111/j.1365-2966.2010.17983.x](http://dx.doi.org/10.1111/j.1365-2966.2010.17983.x)) to the local standard of rest (LSR).  Note that the value of the solar motion through the LSR remains poorly determined.

### Output

The 3-tuple $(u, v, w)$

  * $u$: velocity (km/s) positive toward the Galactic *anti*center
  * $v$: velocity (km/s) positive in the direction of Galactic rotation
  * $w$: velocity (km/s) positive toward the North Galactic Pole

### Method

Follows the general outline of Johnson & Soderblom (1987, AJ, 93, 864; DOI:[10.1086/114370](http://dx.doi.org/10.1086/114370)) except that $u$ is positive outward toward the Galactic *anti*center, and the J2000 transformation matrix to Galactic coordinates is taken from the introduction to the Hipparcos catalog.

### Example

Compute the U,V,W coordinates for the halo star HD 6755.  Use values from Hipparcos catalog, and correct to the LSR.

```jldoctest
julia> using AstroLib

julia> ra = ten(1,9,42.3)*15.; dec = ten(61,32,49.5);

julia> pmra = 627.89;  pmdec = 77.84; # mas/yr

julia> vrad = -321.4; dis = 129; # distance in parsecs

julia> u, v, w = gal_uvw(ra, dec, pmra, pmdec, vrad, 1e3/dis, lsr=true)
(118.2110474553902, -466.4828898385057, 88.16573278565097)
```

### Notes

This function does not take distance as input.  See "Arguments" section above for how to provide it using parallax argument.

Code of this function is based on IDL Astronomy User's Library.
