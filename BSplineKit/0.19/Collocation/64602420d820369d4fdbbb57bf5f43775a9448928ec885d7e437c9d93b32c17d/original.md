```
collocation_points(
    B::AbstractBSplineBasis,
    method::SelectionMethod = default_method(B),
)
```

Define and return adapted collocation points for evaluation of splines.

The number of returned collocation points is equal to the number of functions in the basis.

Note that if `B` is a [`RecombinedBSplineBasis`](@ref) (adapted for boundary value problems), collocation points are not included at the boundaries, since the boundary conditions are implicitly satisfied by the basis.

In principle, the choice of collocation points is not unique. The selection method can be chosen via the `method` argument. For now, the following  methods are accepted:

  * [`Collocation.AvgKnots()`](@ref);
  * [`Collocation.SameAsKnots()`](@ref), which requires the length of the basis to be equal to the number of knots.

The former is the default, except for periodic B-spline bases ([`PeriodicBSplineBasis`](@ref)) of *even* order $k$, for which `SameAsKnots` is the default. (Note that for odd-order B-splines, this can lead to non-invertible collocation matrices.)

See also [`collocation_points!`](@ref).
