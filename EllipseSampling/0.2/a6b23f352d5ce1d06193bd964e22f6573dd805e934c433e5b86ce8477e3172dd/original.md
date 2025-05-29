```
t_from_arclength(arc_len::Float64, e::Ellipse)
```

Calculates the angle t, between 0 and 2π radians, of the location on an unrotated ellipse, given an arc length, `arc_len`, anticlockwise from the positive major axis along the perimeter of the ellipse. The ellipse's x axis is the major axis. It is recommended to call [`t_from_arclength_general(arc_len::T, a::T, b::T) where T<:Float64`] rather than this function as it handles the case where the major axis of the ellipse is the y axis.

Julia version of the python function `t_from_length` by [John D. Cook](https://www.johndcook.com/blog/2022/11/02/ellipse-rng/).

# Arguments

  * `arc_len`: arc length, between 0.0 and the circumference of the ellipse, anticlockwise from the positive major axis along the perimeter of the ellipse.
  * `e`: a valid [`EllipseSampling.Ellipse`](@ref) struct which defines an ellipse.
