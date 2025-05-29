```
generate_perimeter_point(norm_distance_on_perimeter::T, x_radius::T, y_radius::T, α::T=0.0, Cx::T=0.0, Cy::T=0.0) where T<:Float64
```

An alternate way to call [`generate_perimeter_point(norm_distance_on_perimeter::Float64, e::Ellipse)`](@ref), by supplying the parameters of the ellipse to generate a single point on.

# Arguments

  * `norm_distance_on_perimeter`: a number ∈ [0.0,1.0] which represents the normalised distance on the perimeter of an ellipse. A value of 0.5 corresponds to a point halfway along the ellipse's perimeter, while a value of 0.7 corresponds to a point 70% along the ellipse's perimeter.
  * `x_radius`: radius of the ellipse in the x axis (i.e. when the rotation, `α`, is zero).
  * `y_radius`: radius of the ellipse in the y axis (i.e. when the rotation, `α`, is zero).
  * `α`: an angle in radians (0 to 2π) that the ellipse has been rotated by. A positive value represents an anti-clockwise rotation. Default is `0.0`.
  * `Cx`: the x coordinate of the centre of the ellipse (the translation of the ellipse in the x axis). Default is `0.0`.
  * `Cy`: the y coordinate of the centre of the ellipse (the translation of the ellipse in the y axis). Default is `0.0`.
