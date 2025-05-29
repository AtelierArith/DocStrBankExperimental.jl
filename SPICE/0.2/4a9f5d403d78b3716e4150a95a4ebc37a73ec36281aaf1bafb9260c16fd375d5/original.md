```
et2lst(et, body, lon, typ, timlen=128, ampmlen=128)
```

Given an ephemeris epoch, compute the local solar time for an object on the surface of a body at a specified longitude.

### Arguments

  * `et`: Epoch in seconds past J2000 epoch
  * `body`: ID-code of the body of interest
  * `lon`: Longitude of surface point (radians)
  * `typ`: Type of longitude "PLANETOCENTRIC", etc
  * `timlen`: Available room in output time string (default: 128)
  * `ampmlen`: Available room in output `ampm` string (default: 128)

### Output

  * `hr`: Local hour on a "24 hour" clock
  * `mn`: Minutes past the hour
  * `sc`: Seconds past the minute
  * `time`: String giving local time on 24 hour clock
  * `ampm`: String giving time on A.M./ P.M. scale

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/et2lst_c.html)
