```
spkcvo(target, et, outref, refloc, abcorr, obssta, obsepc, obsctr, obsref)
```

Return the state of a specified target relative to an "observer," where the observer has constant velocity in a specified reference frame.  The observer's state is provided by the calling program rather than by loaded SPK files.

### Arguments

  * `target`: Name of target ephemeris object
  * `et`: Observation epoch
  * `outref`: Reference frame of output state
  * `refloc`: Output reference frame evaluation locus
  * `abcorr`: Aberration correction
  * `obssta`: Observer state relative to center of motion
  * `obsepc`: Epoch of observer state
  * `obsctr`: Center of motion of observer
  * `obsref`: Frame of observer state

### Output

  * `state`: State of target with respect to observer
  * `lt`: One way light time between target and observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcvo_c.html)
