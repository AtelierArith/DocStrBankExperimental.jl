```
FDKplan{C,I,H,V}
```

Struct type for storing FDK plan.

The `view_weight` can include (products of)

  * Parker weighting for short scans
  * view-wise CBCT weighting from `fdk_weight_cyl`
  * `dβ` weighting for possibly nonuniform angles from `_angle_weights`
