```
spkezp(targ, et, ref, abcorr, obs)
```

Return the position of a target body relative to an observing body, optionally corrected for light time (planetary aberration) and stellar aberration.

### Arguments

  * `targ`: Target body
  * `et`: Observer epoch
  * `ref`: Reference frame of output state vector
  * `abcorr`: Aberration correction flag
  * `obs`: Observing body

### Output

  * `ptarg`: Position of target
  * `lt`: One way light time between observer and target

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkezp_c.html)
