```
getfov(instid, room=10, shapelen=128, framelen=128)
```

Return the field-of-view (FOV) parameters for a specified instrument. The instrument is specified by its NAIF ID code.

### Arguments

  * `instid`: NAIF ID of an instrument
  * `room`: Maximum number of vectors that can be returned (default: 10)
  * `shapelen`: Space available in the string `shape` (default: 128)
  * `framelen`: Space available in the string `frame` (default: 128)

### Output

Returns a tuple consisting of

  * `shape`: Instrument FOV shape
  * `frame`: Name of the frame in which FOV vectors are defined
  * `bsight`: Boresight vector
  * `bounds`: FOV boundary vectors

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/getfov_c.html)
