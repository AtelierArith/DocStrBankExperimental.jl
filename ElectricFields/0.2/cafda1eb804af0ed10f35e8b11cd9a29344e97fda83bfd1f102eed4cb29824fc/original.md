```
DispersedField(f, de; spline_order=7, Bfs=20/period(F))
```

Convenience constructor for [`DispersedField`](@ref) that automatically finds the appropriate time span for `f` after it has been dispersed through `de`, and then fits a [`BSpline`](@ref) to the resultant vector potential, such that [`vector_potential`](@ref) and [`field_amplitude`](@ref) can be evaluated at arbitrary times. The number of knots can be influenced by the "sampling frequency" `Bfs`.
