```
spkapo(targ, et, ref, sobs, abcorr)
```

Return the position of a target body relative to an observer, optionally corrected for light time and stellar aberration.

### Arguments

  * `targ`: Target body
  * `et`: Observer epoch
  * `ref`: Inertial reference frame of observer's state
  * `sobs`: State of observer wrt. solar system barycenter
  * `abcorr`: Aberration correction flag

### Output

  * `ptarg`: Position of target
  * `lt`: One way light time between observer and target

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkapo_c.html)
