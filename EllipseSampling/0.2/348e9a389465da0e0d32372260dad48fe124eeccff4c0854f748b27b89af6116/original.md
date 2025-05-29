```
t_from_arclength_general(arc_len::Float64, e::Ellipse)
```

Generalised version of [`t_from_arclength(arc_len::Float64, e::Ellipse)`](@ref) which handles cases where either of the x and y axes are the major axis.

# Arguments

  * `arc_len`: arc length, between 0.0 and the circumference of the ellipse, anticlockwise from the positive major axis along the perimeter of the ellipse.
  * `e`: a valid [`EllipseSampling.Ellipse`](@ref) struct which defines an ellipse.
