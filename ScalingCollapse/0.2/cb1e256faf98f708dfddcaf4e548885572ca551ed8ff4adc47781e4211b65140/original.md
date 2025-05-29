```
MultipleSplines(; N_steps::Int=100, weight_density::Bool=true)
```

Quality function that uses a spline interpolation to calculate the quality of a scaling.

# How does it work?

TO BE DOCUMENTED

# Keyword arguments

  * `N_steps::Int=100`: Number of points used in the interval to calculate the quality.
  * `weight_density::Bool=true`: If `true`, the quality is weighted by the density of data points in the interval.
