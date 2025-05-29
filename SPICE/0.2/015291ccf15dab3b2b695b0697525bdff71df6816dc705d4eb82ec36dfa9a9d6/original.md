```
spksub!(newh, handle, descr, ident, start, stop)
```

Extract a subset of the data in an SPK segment into a separate segment.

### Arguments

  * `newh`: Handle of new segment
  * `handle`: Handle of source segment
  * `descr`: Descriptor of source segment
  * `ident`: Identifier of source segment
  * `start`: Beginning (initial epoch) of subset
  * `stop`: End (final epoch) of subset

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spksub_c.html)
