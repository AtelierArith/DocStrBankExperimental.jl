```
ConfigSystem(ndim::Int,gravity::Vector{Float64},num_params::NumParams)
```

Additional system information to define this problem.

## Fields

  * `ndim`: Dimension of this problem. Choices are 2 or 3
  * `gravity`: Non-dimensional gravity. It is in [x,y,z] direction. So if we're   describing a 2d problem with gravity pointing downward, it should be [0.,-1.,0.]
  * `num_params`: Refer to type `NumParams`
