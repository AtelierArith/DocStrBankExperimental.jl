```julia
construct_interpolations(x, y; method, order, extrapolation)

```

Construct interpolation of N-D array `y` along its last dimension on grid `x`. `method` specifies the interpolation algorithm, which can be either "BSpline" or "Gridded". If `x` is an `AbstractRange`, the default method is "BSpline", otherwise the default `method` is "Gridded". `order` is the interpolation order. If `x` is `AbstractRange`, the default order is 2, otherwise the default order is 1. `extrapolation` specifies the extrapolation methods, which defines what happens if you try to index into the interpolation object with coordinates outside of its bounds in any dimension. The implemented extrapolation methods are "line", "flat", or you can pass a constant to be used as a "fill" value returned for any out-of-bounds evaluation. The default value is 0.
