```
spkpos(targ, et, ref, abcorr, obs)
```

Return the position of a target body relative to an observing body, optionally corrected for light time (planetary aberration) and stellar aberration.

### Arguments

  * `targ`: Target body name
  * `et`: Observer epoch
  * `ref`: Reference frame of output position vector
  * `abcorr`: Aberration correction flag
  * `obs`: Observing body name

### Output

  * `ptarg`: Position of target
  * `lt`: One way light time between observer and target

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkpos_c.html)
