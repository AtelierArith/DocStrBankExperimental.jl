```
dwt!(y, x, wt::OrthoFilter[, L=maxtransformlevels(x)])

dwt!(y, wt::GLS[, L=maxtransformlevels(x)])
```

Same as `dwt` but without array allocation. Perform "out of place" transform with a filter, or a inplace transform with a lifting scheme. The difference between the filter and lifting methods is due to the structure of the transform algorithms.

**See also:** `idwt!`
