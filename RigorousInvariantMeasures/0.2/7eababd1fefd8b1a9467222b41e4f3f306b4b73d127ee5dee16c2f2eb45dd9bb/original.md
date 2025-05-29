```
nonzero_on(B::Ulam, (a, b))
```

Returns the indices of the elements of the Ulam basis that intersect with the interval y We do not assume an order of a and b; this should not matter unless the preimages are computed with very low accuracy. We assume, though, that y comes from the (possibly inexact) numerical approximation of an interval in $[0,1]$, i.e., we restrict to $y \cap [0,1]$
