```
et2utc(et, format, prec)
```

Convert an input time from ephemeris seconds past J2000 to Calendar, Day-of-Year, or Julian Date format, UTC.

### Arguments

  * `et`: Input epoch, given in ephemeris seconds past J2000
  * `format`: Format of output epoch. It may be any of the following:

      * `:C`: Calendar format, UTC
      * `:D`: Day-of-Year format, UTC
      * `:J`: Julian Date format, UTC
      * `:ISOC`: ISO Calendar format, UTC
      * `:ISOD`: ISO Day-of-Year format, UTC
  * `prec`: Digits of precision in fractional seconds or days

### Output

Returns an output time string equivalent to the input epoch, in the specified format.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/et2utc_c.html)
