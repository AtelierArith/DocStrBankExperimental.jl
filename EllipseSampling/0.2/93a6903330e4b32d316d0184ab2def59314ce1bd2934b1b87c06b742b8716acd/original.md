```
generate_N_clustered_points(num_points::Int, x_radius::T, y_radius::T, α::T=0.0, Cx::T=0.0, Cy::T=0.0; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.0) where T<:Float64
```

An alternate way to call [`generate_N_clustered_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.)`](@ref), by supplying the parameters of the ellipse to generate points on.

# Arguments

  * `num_points`: a positive integer number of points to generate that are equally spaced on the ellipse.
  * `x_radius`: radius of the ellipse in the x axis (i.e. when the rotation, `α`, is zero).
  * `y_radius`: radius of the ellipse in the y axis (i.e. when the rotation, `α`, is zero).
  * `α`: an angle in radians (0 to 2π) that the ellipse has been rotated by. A positive value represents an anti-clockwise rotation. Default is `0.0`.
  * `Cx`: the x coordinate of the centre of the ellipse (the translation of the ellipse in the x axis). Default is `0.0`.
  * `Cy`: the y coordinate of the centre of the ellipse (the translation of the ellipse in the y axis). Default is `0.0`.

# Keyword Arguments

  * `start_point_shift`: a number ∈ [0.0,1.0]. Default is `rand()` (defined on [0.0,1.0]), meaning that, by default, every time this function is called a different set of points will be generated.
  * `sqrt_distortion`: a number ∈ [0.0,1.0]. Default is `0.0`, meaning that, by default, this function will evenly space points on the the ellipse `e` with respect to the parameter `t`.
