```
common_denominator(x::SimpleRatio, ys::SimpleRatio...)
```

Return the equivalent of `(x, ys...)` but using a common denominator. This can be useful to avoid overflow.

!!! info
    This function is quite slow.  In performance-sensitive contexts where the ratios are constructed with literal constants, it is better to ensure a common denominator at the time of original construction.

