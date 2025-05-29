```
generate_N_equally_spaced_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand())
```

Generates `num_points` equally spaced points on an ellipse defined by the parameters contained within `e`. The points are returned as an array with two rows and `num_points` columns, with each point stored in a column.

# Arguments

  * `num_points`: a positive integer number of points to generate that are equally spaced on the ellipse.
  * `e`: a valid [`EllipseSampling.Ellipse`](@ref) struct which defines an ellipse.

# Keyword Arguments

  * `start_point_shift`: a number ∈ [0.0,1.0]. Default is `rand()` (defined on [0.0,1.0]), meaning that, by default, every time this function is called a different set of points will be generated.

# Details

Points are sampled anti-clockwise around the ellipse starting from the most positive vertex on the major axis prior to any rotation. After a rotation is applied, this vertex may no longer be the most positive vertex on the major axis. Vertex here means the two endpoints that lie on the major axis and intersect the ellipse. If `start_point_shift=0.0` then the first point on the equally spaced points will be placed on the most positive vertex on the major axis prior to any rotation.

Equal spacing of points on the ellipse is with respect to arc length. The position of the first point placed on the ellipse can be shifted by `start_point_shift`, defined on [0.0,1.0], allowing the set of possible points generated for a given `num_points` to cover the full perimeter. This shift is normalised so that when `start_point_shift=1.0`, the position of the first point placed on the ellipse is equal to the position of the second point placed on the ellipse when `start_point_shift=0.0`.
