```
t_from_arclength_general(arc_len::T, a::T, b::T, x_radius::T, y_radius::T) where T<:Float64
```

Generalised version of [`t_from_arclength(arc_len::T, a::T, b::T) where T<:Float64`](@ref) which handles cases where either of the x and y axes are the major axis.

# Arguments

  * `arc_len`: arc length, between 0.0 and the circumference of the ellipse, anticlockwise from the positive major axis along the perimeter of the ellipse.
  * `a`: radius of the ellipse's major axis.
  * `b`: radius of the ellipse's minor axis.
  * `x_radius`: radius of the ellipse in the x axis (i.e. when the rotation, `α`, is zero).
  * `y_radius`: radius of the ellipse in the y axis (i.e. when the rotation, `α`, is zero).
