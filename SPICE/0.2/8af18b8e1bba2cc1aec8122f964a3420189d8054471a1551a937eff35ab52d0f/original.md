```
dskw02(handle, center, surfid, dclass, frame, corsys, corpar, mncor1, mxcor1,
       mncor2, mxcor2, mncor3, mxcor3, first, last, vrtces, plates, spaixd, spaixi)
```

Write a type 2 segment to a DSK file.

### Arguments

  * `handle`: Handle assigned to the opened DSK file
  * `center`: Central body ID code
  * `surfid`: Surface ID code
  * `dclass`: Data class
  * `frame`: Reference frame
  * `corsys`: Coordinate system code
  * `corpar`: Coordinate system parameters
  * `mncor1`: Minimum value of first coordinate
  * `mxcor1`: Maximum value of first coordinate
  * `mncor2`: Minimum value of second coordinate
  * `mxcor2`: Maximum value of second coordinate
  * `mncor3`: Minimum value of third coordinate
  * `mxcor3`: Maximum value of third coordinate
  * `first`: Coverage start time
  * `last`: Coverage stop time
  * `nv`: Number of vertices
  * `vrtces`: Vertices
  * `np`: Number of plates
  * `plates`: Plates
  * `spaixd`: Double precision component of spatial index
  * `spaixi`: Integer component of spatial index

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskw02_c.html)
