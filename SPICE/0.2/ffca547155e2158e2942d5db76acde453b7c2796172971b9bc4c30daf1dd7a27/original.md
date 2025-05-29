```
spkuds(descr)
```

Unpack the contents of an SPK segment descriptor.

### Arguments

  * `descr`: An SPK segment descriptor

### Output

  * `body`: The NAIF ID code for the body of the segment
  * `center`: The center of motion for body
  * `frame`: The ID code for the frame of this segment
  * `type`: The type of SPK segment
  * `first`: The first epoch for which the segment is valid
  * `last`: The last  epoch for which the segment is valid
  * `start`: Beginning DAF address of the segment
  * `stop`: Ending DAF address of the segment

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkuds_c.html)
