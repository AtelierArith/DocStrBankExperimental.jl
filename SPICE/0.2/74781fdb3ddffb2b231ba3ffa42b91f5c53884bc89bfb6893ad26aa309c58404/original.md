```
oscltx(state, et, mu)
```

Determine the set of osculating conic orbital elements that corresponds to the state (position, velocity) of a body at some epoch. In addition to the classical elements, return the true anomaly, semi-major axis, and period, if applicable.

### Arguments

  * `state`: State of body at epoch of elements
  * `et`: Epoch of elements
  * `mu`: Gravitational parameter (GM) of primary body

### Output

Returns the extended set of classical conic elements:

  * `rp`: Perifocal distance.
  * `ecc`: Eccentricity.
  * `inc`: Inclination.
  * `lnode`: Longitude of the ascending node.
  * `argp`: Argument of periapsis.
  * `m0`: Mean anomaly at epoch.
  * `t0`: Epoch.
  * `mu`: Gravitational parameter.
  * `nu`: True anomaly at epoch.
  * `a`: Semi-major axis. A is set to zero if it is not computable.
  * `tau`: Orbital period. Applicable only for elliptical orbits. Set to zero otherwise.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/oscltx_c.html)
