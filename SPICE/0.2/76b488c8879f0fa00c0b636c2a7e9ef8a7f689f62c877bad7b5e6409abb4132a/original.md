```
spkez(targ, et, ref, abcorr, obs)
```

Return the state (position and velocity) of a target body relative to an observing body, optionally corrected for light time (planetary aberration) and stellar aberration.

### Arguments

  * `targ`: Target body
  * `et`: Observer epoch
  * `ref`: Reference frame of output state vector
  * `abcorr`: Aberration correction flag
  * `obs`: Observing body

### Output

  * `starg`: State of target
  * `lt`: One way light time between observer and target

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkez_c.html)
