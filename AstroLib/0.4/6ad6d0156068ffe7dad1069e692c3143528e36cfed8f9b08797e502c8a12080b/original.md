```
sunpos(jd[, radians=false]) -> ra, dec, elong, obliquity
```

### Purpose

Compute the right ascension and declination of the Sun at a given date.

### Arguments

  * `jd`: the Julian date of when you want to calculate Sun position.  It can be either a scalar or a vector.  Use `jdcnv` to get the Julian date for a given date and time.
  * `radians` (optional boolean keyword): if set to `true`, all output quantities are given in radians.  The default is `false`, so all quantities are given in degrees.

### Output

The 4-tuple `(ra, dec, elong, obliquity)`:

  * `ra`: the right ascension of the Sun at that date
  * `dec`: the declination of the Sun at that date
  * `elong`: ecliptic longitude of the Sun at that date
  * `obliquity`: the obliquity of the ecliptic

All quantities are given in degrees, unless `radians` keyword is set to `true` (see "Arguments" section).  If `jd` is an array, arrays of the same given as `jd` are returned.

### Method

Uses a truncated version of Newcomb's Sun.  Adapted from the IDL routine SUN_POS by CD Pike, which was adapted from a FORTRAN routine by B. Emerson (RGO).

### Example

  * Find the apparent right ascension and declination of the Sun on May 1, 1982

    ```jldoctest
    julia> using AstroLib

    julia> adstring(sunpos(jdcnv(1982, 5, 1))[1:2], precision=2)
    " 02 31 32.614  +14 54 34.92"
    ```

    The Astronomical Almanac gives `02 31 32.58 +14 54 34.9` so the error for this case is < 0.5".
  * Plot the apparent right ascension, in hours, and declination of the Sun, in degrees, for every day in 2016.  Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting.

    ```julia
    using Plots
    using Dates

    days = DateTime(2016):Day(1):DateTime(2016, 12, 31);
    ra, declin = sunpos(jdcnv.(days));
    plot(days, ra/15); plot(days, declin)
    ```

### Notes

Patrick Wallace (Rutherford Appleton Laboratory, UK) has tested the accuracy of a C adaptation of the present algorithm and found the following results.  From 1900-2100 `sunpos` gave 7.3 arcsec maximum error, 2.6 arcsec RMS.  Over the shorter interval 1950-2050 the figures were 6.4 arcsec max, 2.2 arcsec RMS.

The returned `ra` and `dec` are in the given date's equinox.

Code of this function is based on IDL Astronomy User's Library.
