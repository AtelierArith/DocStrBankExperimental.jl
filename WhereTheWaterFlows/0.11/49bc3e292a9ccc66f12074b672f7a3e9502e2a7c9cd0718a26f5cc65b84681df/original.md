```
fill_dem(dem, sinks, dir; small=0)
```

Fill the pits of a DEM (apply this after applying "drainpits", which is done by default in `waterflows`). Returns the filled DEM.

Notes:

  * this is *not* needed as pre-processing step to use the flow-routing function `waterflows`.
  * routing on a filled DEM will not produce exactly the same flow pattern: on the shores of lakes streams which entered the lake can now go the other way. I suspect on most DEMs the differences will be very minimal.
  * This uses a tree traversal to fill the DEM. It does it depth-first (as it is easier) which may lead to a stack overflow on a large DEM.
