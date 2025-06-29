```
generate_perimeter_point(norm_distance_on_perimeter::Float64, e::Ellipse)
```

Generates a single point on an ellipse defined by the parameters contained within `e`, at distance `norm_distance_on_perimeter` $\times$ `e.circumference` around the circumference. The point is returned as a vector of length two.

# Arguments

  * `norm_distance_on_perimeter`: a number ∈ [0.0,1.0] which represents the normalised distance on the perimeter of an ellipse. A value of `0.5` corresponds to a point halfway along the ellipse's perimeter, while a value of `0.7` corresponds to a point 70% along the ellipse's perimeter.
  * `e`: a valid [`EllipseSampling.Ellipse`](@ref) struct which defines an ellipse.

# Details

Points are sampled anti-clockwise around the ellipse starting from the most positive vertex on the major axis prior to any rotation. After a rotation is applied, this vertex may no longer be the most positive vertex on the major axis. Vertex here means the two endpoints that lie on the major axis and intersect the ellipse. 

Consider a ellipse that has no translation or rotational component. If the x radius is `2.0` and the y radius is `1.0`, then the x axis is the major axis. Resultantly, a value of `norm_distance_on_perimeter=0.0` will correspond to point `[x,y] = [2.0, 0.0]`. A value of `norm_distance_on_perimeter=0.25`, which corresponds to a $\frac{π}{2}$ anti-clockwise rotation around the ellipse will correspond to point `[x,y] = [0.0, 1.0]`. 

```julia
using EllipseSampling
e = construct_ellipse(2.0, 1.0)
generate_perimeter_point(0.0, e)
generate_perimeter_point(0.25, e)
```

Similarly, if the x radius is `1.0` and the y radius is `2.0`, then the y axis is the major axis. Resultantly, a value of `norm_distance_on_perimeter=0.0` will correspond to point `[x,y] = [0.0, 2.0]`. A value of `norm_distance_on_perimeter=0.25`, which corresponds to a $\frac{π}{2}$ anti-clockwise rotation around the ellipse will correspond to point `[x,y] = [-1.0, 0.0]`. 

```julia
e = construct_ellipse(1.0, 2.0)
generate_perimeter_point(0.0, e)
generate_perimeter_point(0.25, e)
```

In the event that the ellipse is a circle (the major and minor axis have the same radius), points will be sampled anti-clockwise around the ellipse starting from the most positive point on the x radius (prior to any rotation). 

To demonstrate how sampling works when the ellipse is rotated, for simplicity, consider an ellipse that is a circle with radius 1.0, no translational component and an anti-clockwise rotation of $\frac{π}{2}$. In this case the x axis has been rotated anti-clockwise by 90 degrees and so a value of `norm_distance_on_perimeter=0.0` will correspond to point `[x,y] = [0.0, 1.0]`. A value of `norm_distance_on_perimeter=0.25`, which corresponds to a $\frac{π}{2}$ anti-clockwise rotation around the rotated ellipse will correspond to point `[x,y] = [-1.0, 0.0]`. 

```julia
e = construct_ellipse(1.0, 1.0, pi/2)
generate_perimeter_point(0.0, e)
generate_perimeter_point(0.25, e)
```

## Random sampling

This function can be easily used to generate uniform random samples from an ellipse by first sampling N points from a uniform distribution defined on [0,1] and then calling this function for each point 1:N.

For example using:

```julia
using EllipseSampling
e = construct_ellipse(2.0,1.0)
N = 100
samples = rand(N)
points = generate_perimeter_point.(samples, Ref(e))
```

Note, here we wrap the ellipse struct `e` in `Ref` so that Julia does not try to broadcast over `e` as well. To get the points generated in this fashion in the same column-wise format as points generated by [`generate_N_equally_spaced_points`](@ref) we can use:

```julia
points = reduce(hcat, points)
```

Other distributions defined on [0,1] can be used to generate points on the ellipse's perimeter in a similar fashion.
