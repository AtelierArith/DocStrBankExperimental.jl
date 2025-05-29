```
add_default_local_refinement(spline_grid)
```

Refine in the default way in every dimension, i.e. bisecting every non-trivial knot span. Yields a spline grid with a `LocallyRefinedControlPoints` object for the `control_points` field.
