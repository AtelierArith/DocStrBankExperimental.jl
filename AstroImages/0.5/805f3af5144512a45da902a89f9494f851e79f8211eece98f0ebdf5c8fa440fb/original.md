```
wcs(img)
```

Computes and returns a list of World Coordinate System WCSTransform objects from WCS.jl. The resultss are cached after the first call, so subsequent calls are fast. Modifying a WCS header invalidates this cache automatically, so users should call `wcs(...)` each time rather than keeping the WCSTransform object around.
