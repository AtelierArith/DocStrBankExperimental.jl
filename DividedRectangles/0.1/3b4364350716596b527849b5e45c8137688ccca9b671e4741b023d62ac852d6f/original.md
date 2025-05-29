```
optimize(f, a::Vector{Float64}, b::Vector{Float64}; max_iterations::Int = 100, min_radius::Float64 = 1e-5)
```

The primary optimization routine of the DividedRectangles module. It uses the DIRECT algorithm to search for the global minimum of the objective function `f` over a bounded search space defined by `a` and `b`.

# Arguments

  * `f`: The objective function to be minimized. Must be defined for inputs in ℝⁿ.
  * `a::Vector{Float64}`: A vector of lower bounds for the search space.
  * `b::Vector{Float64}`: A vector of upper bounds for the search space.
  * `max_iterations::Int`: (Optional) The maximum number of iterations for the DIRECT algorithm (default is 100).
  * `min_radius::Float64`: (Optional) The minimum radius below which hyperrectangles are no longer subdivided (default is 1e-5).

# Returns

  * A vector of `Float64` representing the best design (i.e., the point in the original search space) found by the DIRECT algorithm.
