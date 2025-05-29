```
ckgpav(inst, sclkdp, tol, ref)
```

Get pointing (attitude) and angular velocity for a specified spacecraft clock time.

### Arguments

  * `inst`: NAIF ID of instrument, spacecraft, or structure
  * `sclkdp`: Encoded spacecraft clock time
  * `tol`: Time tolerance
  * `ref`: Reference frame

### Outputs

Returns `nothing` if the requested pointing is not available or

  * `cmat`: C-matrix pointing data
  * `av`: Angular velocity vector
  * `clkout`: Output encoded spacecraft clock time

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckgpav_c.html)
