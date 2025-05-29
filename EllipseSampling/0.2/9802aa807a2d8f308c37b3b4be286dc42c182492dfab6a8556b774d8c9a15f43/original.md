```
x_parametric_equation(t::T, x_radius::T, y_radius::T, α::T=0.0, Cx::T=0.0) where T<:Float64
```

Implements the parametric equation for variable x of a translated and rotated ellipse, $x(t)$, where t is an angle between 0 and 2π radians.

# Arguments

  * `t`: an angle between 0 and 2π radians that defines the x location on the ellipse.
  * `x_radius`: radius of the ellipse in the x axis (i.e. when the rotation, `α`, is zero).
  * `y_radius`: radius of the ellipse in the y axis (i.e. when the rotation, `α`, is zero).
  * `α`: an angle in radians (0 to 2π) that the ellipse has been rotated by. A positive value represents an anti-clockwise rotation. Default is `0.0`.
  * `Cx`: the x coordinate of the centre of the ellipse (the translation of the ellipse in the x axis). Default is `0.0`.
