```
spkltc(targ, et, ref, abcorr, stobs)
```

Return the state (position and velocity) of a target body relative to an observer, optionally corrected for light time, expressed relative to an inertial reference frame.

### Arguments

  * `targ`: Target body
  * `et`: Observer epoch
  * `ref`: Inertial reference frame of output state
  * `abcorr`: Aberration correction flag
  * `stobs`: State of the observer relative to the SSB

### Output

  * `starg`: State of target
  * `lt`: One way light time between observer and target
  * `dlt`: Derivative of light time with respect to time

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkltc_c.html)
