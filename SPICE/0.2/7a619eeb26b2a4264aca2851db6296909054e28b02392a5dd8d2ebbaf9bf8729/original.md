```
eqncpv(et, epoch, eqel, rapol, decpol)
```

Compute the state (position and velocity of an object whose trajectory is described via equinoctial elements relative to some fixed plane (usually the equatorial plane of some planet).

### Arguments

  * `et`: Epoch in seconds past J2000 to find state
  * `epoch`: Epoch of elements in seconds past J2000
  * `eqel`: Array of equinoctial elements
  * `rapol`: Right Ascension of the pole of the reference plane
  * `decpol`: Declination of the pole of the reference plane

### Output

Returns the state of the object described by `eqel`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/eqncpv_c.html)
