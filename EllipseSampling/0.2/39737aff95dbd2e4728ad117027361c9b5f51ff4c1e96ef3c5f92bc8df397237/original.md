```
t_from_arclength(arc_len::T, a::T, b::T) where T<:Float64
```

An alternate way to call [`t_from_arclength(arc_len::Float64, e::Ellipse)`](@ref).

# Arguments

  * `arc_len`: arc length, between 0.0 and the circumference of the ellipse, anticlockwise from the positive major axis along the perimeter of the ellipse.
  * `a`: radius of the ellipse's major axis.
  * `b`: radius of the ellipse's minor axis.
