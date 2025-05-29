```
center, radius = boundingsphere(pts [, algorithm=WelzlPivot()])
```

Compute the smallest sphere that contains each point in `pts`.

# Arguments

  * pts: A list of points. Points should be vectors with floating point entries.
  * algorithm: An optional algorithm to do the computation. See names(BoundingSphere) to get
