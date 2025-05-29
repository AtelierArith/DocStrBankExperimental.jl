```
SplineGrid(spline_dimensions::NTuple{Nin, <:SplineDimension{Tv, Ti}}, Nout::Integer)::SplineGrid{Nin, Tv, Ti} where {Nin, Tv, Ti}
```

Define a `SplineGrid` from an NTuple of spline dimensions and the number of output dimensions.

## Inputs

  * `spline_dimensions`: an NTuple of spline dimensions
  * `Nout`: The number of output dimensions. I.e. the control points and thus the spline live in ℝ^Nout.
