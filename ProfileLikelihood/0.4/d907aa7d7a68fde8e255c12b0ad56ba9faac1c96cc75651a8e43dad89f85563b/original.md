```
struct RegularGrid{N,B,R,S,T} <: AbstractGrid{N,B,T}
```

Struct for a grid in which each parameter is regularly spaced. 

# Fields

  * `lower_bounds::B`: Lower bounds for each parameter.
  * `upper_bounds::B`: Upper bounds for each parameter.
  * `resolution::R`: Number of grid points for each parameter. If `R <: Number`, then the same number of grid points is used for each parameter.
  * `step_sizes::S`: Grid spacing for each parameter.

# Constructor

You can construct a `RegularGrid` using `RegularGrid(lower_bounds, upper_bounds, resolution)`.
