```
spkcvt(trgsta, trgepc, trgctr, trgref, et, outref, refloc, abcorr, obsrvr)
```

Return the state, relative to a specified observer, of a target having constant velocity in a specified reference frame. The target's state is provided by the calling program rather than by loaded SPK files.

### Arguments

  * `trgsta`: Target state relative to center of motion
  * `trgepc`: Epoch of target state
  * `trgctr`: Center of motion of target
  * `trgref`: Frame of target state
  * `et`: Observation epoch
  * `outref`: Reference frame of output state
  * `refloc`: Output reference frame evaluation locus
  * `abcorr`: Aberration correction
  * `obsrvr`: Name of observing ephemeris object

### Output

  * `state`: State of target with respect to observer
  * `lt`: One way light time between target and observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcvt_c.html)
