```
spkpvn(handle, descr, et)
```

For a specified SPK segment and time, return the state (position and velocity) of the segment's target body relative to its center of motion.

### Arguments

  * `handle`: File handle
  * `descr`: Segment descriptor
  * `et`: Evaluation epoch

### Output

  * `ref`: Segment reference frame ID code
  * `state`: Output state vector
  * `center`: Center of state

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkpvn_c.html)
