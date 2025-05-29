```
Interpolator2D{T, S, U, F}
```

A 2D interpolation structure where:

  * `x_vals`: grid in the x-direction (e.g., expiry),
  * `y_vals`: grid in the y-direction (e.g., strike),
  * `y_interps`: interpolators in the y-direction, one per x,
  * `build_x_interp`: a function `y ↦ x-interpolator` built from applying all y-interpolators at `y`.
