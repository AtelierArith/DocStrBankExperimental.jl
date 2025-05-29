```
IDWInterpolator(factors; leafsize=10, k=8, power=1, reg=0, conf_dist=1e-12)
```

Use Shepard Inverse Distance Weighing interpolation scheme to increase resolution of a mesh.

`factors` represents the level of "zoom", so an input mesh of size `(10, 10)` with factors `(2, 2)` will have an output size of `(20, 20)`. If only an integer is provided, it will be used as the factor for every axis.

The interpolator can be called with some additional parameters:

  * `leaf_size` determines at what number of points to stop splitting the tree further,
  * `k` which is the number of nearest neighbors to be considered,
  * `power` is the exponent for distance in the weighing factor,
  * `reg` is the offset for the weighing factor in denominator,
  * `conf_dist` is the distance below which two points would be considered as the same point.

# Examples

```jldoctest
julia> IDWInterpolator(2, k=2)([1 0; 0 1])
4×4 Matrix{Float64}:
 1.0   0.75      0.25      0.0
 0.75  0.690983  0.309017  0.25
 0.25  0.309017  0.690983  0.75
 0.0   0.25      0.75      1.0

julia> IDWInterpolator(3, 1; k=2, power=4)([1 0; 0 1])
6×2 Matrix{Float64}:
 1.0        0.0
 1.0        0.0
 0.941176   0.0588235
 0.0588235  0.941176
 0.0        1.0
 0.0        1.0
```
