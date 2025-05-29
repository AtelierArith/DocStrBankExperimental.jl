```
spkaps(targ, et, ref, abcorr, stobs, accobs)
```

Given the state and acceleration of an observer relative to the solar system barycenter, return the state (position and velocity) of a target body relative to the observer, optionally corrected for light time and stellar aberration. All input and output vectors are expressed relative to an inertial reference frame.

Users normally should call the high-level API routines [`spkezr`](@ref) or [`spkez`](@ref) rather than this routine.

### Arguments

  * `targ`: Target body.
  * `et`: Observer epoch.
  * `ref`: Inertial reference frame of output state.
  * `abcorr`: Aberration correction flag.
  * `stobs`: State of the observer relative to the SSB.
  * `accobs`: Acceleration of the observer relative to the SSB.

### Output

  * `starg`: State of target.
  * `lt`: One way light time between observer and target.
  * `dlt`: Derivative of light time with respect to time.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkaps_c.html)
