```
longitude_circshift(X::ClimArray [, l]; wrap = true) → Y::ClimArray
```

Perform the same action as `Base.circshift`, but only for the longitudinal dimension of `X` with shift `l`. If `wrap = true` the longitudes are wrapped to (-180, 180) degrees using the modulo operation.

If `l` is not given, it is as much as necessary so that all longitudes > 180 are circshifted (and also wrapped if `wrap`).

If `X` has a `CoordinateSpace`, then no circshift is happening (the lon-lat are one dimension), but the longitude is still shifted.
