```
bprecess(ra, dec[, epoch]) -> ra1950, dec1950
bprecess(ra, dec, muradec[, parallax=parallax, radvel=radvel]) -> ra1950, dec1950
```

### Purpose

Precess positions from J2000.0 (FK5) to B1950.0 (FK4).

### Explanation

Calculates the mean place of a star at B1950.0 on the FK4 system from the mean place at J2000.0 on the FK5 system.

`bprecess` function has two methods, one for each of the following cases:

  * the proper motion is known and non-zero
  * the proper motion is unknown or known to be exactly zero (i.e. extragalactic radio sources).  Better precision can be achieved in this case by inputting the epoch of the original observations.

### Arguments

The function has 2 methods.  The common mandatory arguments are:

  * `ra`: input J2000 right ascension, in degrees.
  * `dec`: input J2000 declination, in degrees.

The two methods have a different third argument (see "Explanation" section for more details).  It can be one of the following:

  * `muradec`: 2-element vector containing the proper motion in seconds of arc per tropical *century* in right ascension and declination.
  * `epoch`: scalar giving epoch of original observations.

If none of these two arguments is provided (so `bprecess` is fed only with right ascension and declination), it is assumed that proper motion is exactly zero and `epoch = 2000`.

If it is used the method involving `muradec` argument, the following keywords are available:

  * `parallax` (optional numerical keyword): stellar parallax, in seconds of arc.
  * `radvel` (optional numerical keyword): radial velocity in km/s.

Right ascension and declination can be passed as the 2-tuple `(ra, dec)`.  You can also pass `ra`, `dec`, `parallax`, and `radvel` as arrays, all of the same length N.  In that case, `muradec` should be a matrix 2×N.

### Output

The 2-tuple of right ascension and declination in 1950, in degrees, of input coordinates is returned.  If `ra` and `dec` (and other possible optional arguments) are arrays, the 2-tuple of arrays `(ra1950, dec1950)` of the same length as the input coordinates is returned.

### Method

The algorithm is taken from the Explanatory Supplement to the Astronomical Almanac 1992, page 186.  See also Aoki et al (1983), A&A, 128, 263.  URL: http://adsabs.harvard.edu/abs/1983A%26A...128..263A.

### Example

The SAO2000 catalogue gives the J2000 position and proper motion for the star HD 119288.  Find the B1950 position.

  * RA(2000) = 13h 42m 12.740s
  * Dec(2000) = 8d 23' 17.69''
  * Mu(RA) = -.0257 s/yr
  * Mu(Dec) = -.090 ''/yr

```jldoctest
julia> using AstroLib

julia> muradec = 100*[-15*0.0257, -0.090]; # convert to century proper motion

julia> ra = ten(13, 42, 12.74)*15;

julia> decl = ten(8, 23, 17.69);

julia> adstring(bprecess(ra, decl, muradec), precision=2)
" 13 39 44.526  +08 38 28.63"
```

### Notes

"When transferring individual observations, as opposed to catalog mean place, the safest method is to transform the observations back to the epoch of the observation, on the FK4 system (or in the system that was used to to produce the observed mean place), convert to the FK5 system, and transform to the the epoch and equinox of J2000.0" – from the Explanatory Supplement (1992), p. 180

`jprecess` performs the precession to J2000 coordinates.

Code of this function is based on IDL Astronomy User's Library.
