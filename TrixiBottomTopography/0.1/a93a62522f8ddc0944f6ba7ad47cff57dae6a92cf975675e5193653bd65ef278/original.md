```
BilinearBSpline(x, y, Delta, Q, IP)
```

Two dimensional bilinear B-spline structure that contains all important attributes to define a B-Spline interpolation function. These attributes are:

  * `x`: Vector of values in x-direction
  * `y`: Vector of values in y-direction
  * `Delta`: Length of one side of a single patch in the given data set. A patch is the area between          two consecutive `x` and `y` values. The value `Delta` corresponds to the distance          between two consecutive values in x-direction. As we are only considering Cartesian          grids, `Delta` is equal for all patches in x and y-direction
  * `Q`: Matrix which contains the control points
  * `IP`: Coefficients matrix
