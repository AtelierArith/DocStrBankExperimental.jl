```
generate_N_clustered_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.0)
```

Generates `num_points` spaced points on an ellipse defined by the parameters contained within `e`. The points are returned as an array with two rows and `num_points` columns, with each point stored in a column.

# Arguments

  * `num_points`: a positive integer number of points to generate that are spaced on the ellipse.
  * `e`: a valid [`EllipseSampling.Ellipse`](@ref) struct which defines an ellipse.

# Keyword Arguments

  * `start_point_shift`: a number ∈ [0.0,1.0]. Default is `rand()` (defined on [0.0,1.0]), meaning that, by default, every time this function is called a different set of points will be generated.
  * `sqrt_distortion`: a number ∈ [0.0,1.0]. Default is `0.0`, meaning that, by default, this function will evenly space points on the the ellipse `e` with respect to the parameter `t`.

# Details

Points are sampled in the same fashion as in [`generate_N_equally_spaced_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand())`](@ref), except that the spacing of them is dependent on the parameter `sqrt_distortion`. If `sqrt_distortion == 1.0` then these points are equally spaced with respect to the arc length. If `sqrt_distortion == 0.0` then these points are equally spaced with respect to the parameter `t` in the parameteric equations for the x and y locations on an ellipse ([`x_parametric_equation(t::T, e::Ellipse) where T<:Float64`](@ref) and [`y_parametric_equation(t::T, e::Ellipse) where T<:Float64`](@ref)). Varying this parameter between `0.0` and `1.0` allows all of the spacings between these two extremes to be obtained.

The impact of using this function is that for all values of `sqrt_distortion < 1.0`, points generated will be more clustered around the vertexes of the ellipse on the major axis (i.e. the region of greatest curvature). The strength of this clustering increases as `sqrt_distortion` $\to 0.0$. The strength of the clustering is also dependent on the relative magnitudes of the major and minor axis radii. If the major and minor axis have the same radii, then the ellipse is a circle and no clustering will be observed, irrespective of the value of `sqrt_distortion`. As the magnitude of the major axis radius increases relative to the minor axis radius, the strength of the clustering will increase. 

This effect is valuable when using an ellipse as a starting point to find a new level set in 2D (that may be an ellipse) that contains the starting ellipse. If we seek to find the new level set by pushing out from the starting ellipse tangentially at each of the generated points then the points that diverge the fastest are located at the region of greatest curvature. If generated points are equally spaced with respect to arc length, then the new level set is likely to be well defined in regions that are approximately parallel to the major axis of the starting ellipse (and with length on a parallel line of similar length to the major axis, particularly for starting ellipses with a significantly larger major axis), but poorly defined in all other regions. The clustering effect is then valuable as it helps to better define the new level set.   

The function works by defining a new ellipse, `e_new` with minor axis radius equal to the supplied ellipse's minor axis radius (`e_new.b == e.b`) and major axis radius as a function of the supplied ellipse's, `e`, major and minor axis radii and the parameter `sqrt_distortion`. Namely, `e_new.a == e.b + sqrt_distortion^2 * (e.a - e.b)`. `e_new` is contained within `e` and can be varied between a circle and `e` using the parameter `sqrt_distortion` ∈ [0.0,1.0]. After defining `e_new` we determine the angle parameters `t_vector` that equally spaces `num_points` on `e_new` with respect to arc length and then find the points on `e` parameterised by the elements of `t_vector`.
