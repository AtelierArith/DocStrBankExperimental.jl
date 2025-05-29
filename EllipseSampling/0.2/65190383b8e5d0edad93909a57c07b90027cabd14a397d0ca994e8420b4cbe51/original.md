```
y_parametric_equation(t::T, e::Ellipse) where T<:Float64
```

Implements the parametric equation for variable y of a translated and rotated ellipse, $y(t)$, where `t` is an angle between 0 and 2π radians.

# Arguments

  * `t`: an angle between 0 and 2π radians that defines the y location on the ellipse.
  * `e`: a valid [`Ellipse`](@ref) struct which defines an ellipse.
