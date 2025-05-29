```
collocation_points!(
    x::AbstractVector, B::AbstractBSplineBasis,
    method::SelectionMethod = default_method(B),
)
```

Fill vector with collocation points for evaluation of splines.

See [`collocation_points`](@ref) for details.
