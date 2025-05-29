```
generate_simplex_grid(resolution::Int, margin::Int = 1) -> Vector{Vector{Float64}}
```

Generates a list of points within the simplex by discretizing the simplex into a grid, excluding points near the boundaries as specified by the margin.

# Arguments

  * `resolution`: The number of divisions along each edge of the simplex. Higher resolution results in more points.
  * `margin`: The number of grid layers to exclude from the edges. Defaults to 1.

# Returns

  * A vector of points, where each point is a vector `[x₁, x₂, x₃]` representing the frequencies of the three strategies at that grid point.

# Notes

  * This function is used to generate points for plotting contour plots within the simplex.
