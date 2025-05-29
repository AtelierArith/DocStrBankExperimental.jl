```
SimplexGridBuilder(; Generator=nothing,
                     tol=1.0e-12,
                     checkexisting=true)
```

Create a SimplexGridBuilder.

  * `Generator`: module corresponding to mesh generator package.  Valid choices are `TetGen` and `Triangulate`, corresponding to the   respective Julia packages.
  * `checkexisting`: whether to check for already existing points
  * `tol`: two points below this tolerance will be merged if `checkexisting` is true
