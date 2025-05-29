```
compute_inface_extreme_point(lmo, direction, x; lazy, kwargs...)
```

LMO-like operation which computes a vertex minimizing in `direction` on the face defined by the current fixings. Fixings are maintained by the oracle (or deduced from `x` itself).
