```
finufft_setpts!(plan, xj [, yj[, zj[, s[, t[, u]]]]])
```

Input nonuniform points for general FINUFFT transform(s).

Given an already-planned `finufft_plan`, this reads in nonuniform point  coordinate arrays `xj` (and `yj` if 2D or 3D, and `zj` if 3D), and additionally in the type 3 case, nonuniform  frequency target coordinate arrays `s` (and `t` if 2D or 3D, and `u` if 3D). Empty arrays may be passed in the case of  unused dimensions. For all types, sorting is done to internally store a  reindexing of points, and for type 3 the spreading and FFTs are planned.  These nonuniform points may then be used for multiple transforms.

# Input

  * `plan`   a `finufft_plan` object for one/many general nonuniform FFTs
  * `xj`     vector of x-coords of all nonuniform points
  * `yj`     empty (if dim<2), or vector of y-coords of all nonuniform points
  * `zj`     empty (if dim<3), or vector of z-coords of all nonuniform points
  * `s`      vector of x-coords of all nonuniform frequency targets
  * `t`      empty (if dim<2), or vector of y-coords of all frequency targets
  * `u`      empty (if dim<3), or vector of z-coords of all frequency targets

Vectors must be `Array{T}` or contiguous `SubArray{T}` (view), where `T` is `Float32` or `Float64`.
