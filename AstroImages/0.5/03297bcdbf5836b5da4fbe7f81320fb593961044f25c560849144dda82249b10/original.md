```
wcs(img, index)
```

Computes and returns a World Coordinate System WCSTransform objects from WCS.jl by index. This is to support files with multiple WCS transforms specified. `wcs(img,1)` is useful for selecting selecting the first WCSTranform object. The resultss are cached after the first call, so subsequent calls are fast. Modifying a WCS header invalidates this cache automatically, so users should call `wcs(...)` each time rather than keeping the WCSTransform object around.
