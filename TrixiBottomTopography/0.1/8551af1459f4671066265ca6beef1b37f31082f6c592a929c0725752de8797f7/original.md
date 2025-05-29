```
CubicBSpline(x, Delta, Q, IP)
```

One dimensional cubic B-spline structure that contains all important attributes to define a B-Spline interpolation function. Similar to [`LinearBSpline`](@ref) These attributes are:

  * `x`: Vector of values in x-direction
  * `Delta`: Length of a single patch in the given data set. A patch is the area between two          consecutive `x` values. The value `Delta` corresponds to the distance between two          consecutive values in x-direction. As we are only considering Cartesian grids, `Delta`          is equal for all patches
  * `Q`: Vector which contains the Control points
  * `IP`: Coefficients matrix
