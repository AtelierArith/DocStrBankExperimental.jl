```
isbounded(eprojmap::ExponentialProjectionMap)
```

Check whether a projection of an exponential map is bounded.

### Input

  * `eprojmap` – projection of an exponential map

### Output

`true` iff the projection of an exponential map is bounded.

### Algorithm

We first check if the left or right projection matrix is zero or the wrapped set is bounded. Otherwise, we check boundedness via [`LazySets._isbounded_unit_dimensions`](@ref).
