```
axis_limits(I) = (i0,i1)
```

yields the limits `i0` and `i1` of index range `I` as a 2-tuple of `Int`'s and such that `i0:i1` represents the same indices as `I` (although not in the same order if `step(I) < 0`). If `step(I)` is not equal to ±1, an `ArgumentError` exception is thrown.
