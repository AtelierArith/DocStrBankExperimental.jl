Given an epoch, return the state vector `[x, y, z, ẋ, ẏ, ż]` (KM,KM/s) of  the body relative to the observer defined by `wrt`. See `spkez` for more  information about the underlying implementation. Use the `dimension` keyword argument to specify whether you want the full state vector, the `Val(:position)`, or the `Val(:velocity)`.

```julia
body(epoch; frame = "J2000", aberration = "none", wrt = naifcode("ssb"), dimension = Val(:all))
```
