```
ltime(etobs, obs, dir, targ)
```

This routine computes the transmit (or receive) time of a signal at a specified target, given the receive (or transmit) time at a specified observer. The elapsed time between transmit and receive is also returned.

### Arguments

  * `etobs`: Epoch of a signal at some observer
  * `obs`: NAIF ID of some observer
  * `dir`: Direction the signal travels ( `"->"` or `"<-"` )
  * `targ`: Time between transmit and receipt of the signal

### Output

  * `ettarg`: Epoch of the signal at the target
  * `obs`: NAIF ID of some observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ltime_c.html)
