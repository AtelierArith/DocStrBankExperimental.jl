```
typeofSrc(x::Int)::SrcType
```

set and return the value of the global `GeoEfficiency.srcType` corresponding to `x`.

  * srcUnknown = -1 also any negative integer treated as so,
  * srcPoint   = 0,
  * srcLine    = 1,
  * srcDisk    = 2,
  * srcVolume  = 3,
  * srcNotPoint = 4 also any greater than 4 integer treated as so.
