```
Climate2Dstep{F <: AbstractFloat}
```

A mutable struct representing a 2D climate time step with various climate-related parameters.

# Keyword arguments

  * `temp::Matrix{F}`: Temperature matrix.
  * `PDD::Matrix{F}`: Positive Degree Days matrix.
  * `snow::Matrix{F}`: Snowfall matrix.
  * `rain::Matrix{F}`: Rainfall matrix.
  * `gradient::F`: Gradient value.
  * `avg_gradient::F`: Average gradient value.
  * `x::Vector{F}`: X-coordinates vector.
  * `y::Vector{F}`: Y-coordinates vector.
  * `ref_hgt::F`: Reference height.
