```
x_parametric_equation(t::T, e::Ellipse) where T<:Float64
```

Implements the parametric equation for variable x of a translated and rotated ellipse, $x(t)$, where t is an angle between 0 and 2π radians.

# Arguments

  * `t`: an angle between 0 and 2π radians that defines the x location on the ellipse.
  * `e`: a valid [`Ellipse`](@ref) struct which defines an ellipse.
