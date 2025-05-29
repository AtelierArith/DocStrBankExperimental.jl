```
oscelt(state, et, mu)
```

Determine the set of osculating conic orbital elements that corresponds to the state (position, velocity) of a body at some epoch.

### Arguments

  * `state`: State of body at epoch of elements
  * `et`: Epoch of elements
  * `mu`: Gravitational parameter (GM) of primary body

### Output

Returns the equivalent conic elements:

  * `rp`: Perifocal distance
  * `ecc`: Eccentricity
  * `inc`: Inclination
  * `lnode`: Longitude of the ascending node
  * `argp`: Argument of periapsis
  * `m0`: Mean anomaly at epoch
  * `t0`: Epoch
  * `mu`: Gravitational parameter

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/oscelt_c.html)
