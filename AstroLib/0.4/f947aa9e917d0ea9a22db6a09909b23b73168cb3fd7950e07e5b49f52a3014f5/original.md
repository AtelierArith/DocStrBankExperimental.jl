```
moonpos(jd[, radians=true]) -> ra, dec, dis, geolong, geolat
```

### Purpose

Compute the right ascension and declination of the Moon at specified Julian date.

### Arguments

  * `jd`: the Julian ephemeris date.  It can be either a scalar or an array
  * `radians` (optional boolean keyword): if set to `true`, then all output angular quantities are given in radians rather than degrees.  The default is `false`

### Output

The 5-tuple `(ra, dec, dis, geolong, geolat)`:

  * `ra`: apparent right ascension of the Moon in degrees, referred to the true equator of the specified date(s)
  * `dec`: the declination of the Moon in degrees
  * `dis`: the distance between the centre of the Earth and the centre of the Moon in kilometers
  * `geolong`: apparent longitude of the moon in degrees, referred to the ecliptic of the specified date(s)
  * `geolat`: apparent longitude of the moon in degrees, referred to the ecliptic of the specified date(s)

If `jd` is an array, then all output quantities are arrays of the same length as `jd`.

### Method

Derived from the Chapront ELP2000/82 Lunar Theory (Chapront-Touze' and Chapront, 1983, 124, 50), as described by Jean Meeus in Chapter 47 of ``Astronomical Algorithms'' (Willmann-Bell, Richmond), 2nd edition, 1998.  Meeus quotes an approximate accuracy of 10" in longitude and 4" in latitude, but he does not give the time range for this accuracy.

Comparison of the IDL procedure with the example in ``Astronomical Algorithms'' reveals a very small discrepancy (~1 km) in the distance computation, but no difference in the position calculation.

### Example

  * Find the position of the moon on April 12, 1992

    ```jldoctest
    julia> using AstroLib

    julia> jd = jdcnv(1992, 4, 12);

    julia> adstring(moonpos(jd)[1:2],precision=1)
    " 08 58 45.23  +13 46 06.1"
    ```

    This is within 1" from the position given in the Astronomical Almanac.
  * Plot the Earth-moon distance during 2016 with sampling of 6 hours.  Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting

    ```julia
    using Dates
    using Plots
    points = DateTime(2016):Dates.Hour(6):DateTime(2017);
    plot(points, moonpos(jdcnv.(points))[3])
    ```

### Notes

Code of this function is based on IDL Astronomy User's Library.
