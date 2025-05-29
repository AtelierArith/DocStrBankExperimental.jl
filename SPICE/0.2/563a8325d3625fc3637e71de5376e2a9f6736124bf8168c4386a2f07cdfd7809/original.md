```
spkcpo(target, et, outref, refloc, abcorr, obspos, obsctr, obsref)
```

Return the state of a specified target relative to an "observer," where the observer has constant position in a specified reference frame. The observer's position is provided by the calling program rather than by loaded SPK files.

### Arguments

  * `target`: Name of target ephemeris object
  * `et`: Observation epoch
  * `outref`: Reference frame of output state
  * `refloc`: Output reference frame evaluation locus
  * `abcorr`: Aberration correction
  * `obspos`: Observer position relative to center of motion
  * `obsctr`: Center of motion of observer
  * `obsref`: Frame of observer position

### Output

  * `state`: State of target with respect to observer
  * `lt`: One way light time between target and observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcpo_c.html)
