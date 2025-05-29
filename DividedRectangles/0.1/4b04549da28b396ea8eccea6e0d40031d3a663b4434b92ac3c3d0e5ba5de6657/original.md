```
direct(f, a::Vector{Float64}, b::Vector{Float64}; max_iterations::Int = 100, min_radius::Float64 = 1e-5)
```

Implements the DIRECT (DIvided RECTangles) algorithm to perform global optimization by iteratively subdividing the search space. The algorithm operates in the normalized unit hypercube [0, 1]^n, where the mapping from the original search space (given by bounds `a` and `b`) to the unit hypercube is performed on-the-fly.

# Arguments

  * `f`: The objective function to be minimized. It should accept a vector of real numbers and return a scalar.
  * `a::Vector{Float64}`: A vector of lower bounds for each dimension of the original search space.
  * `b::Vector{Float64}`: A vector of upper bounds for each dimension of the original search space.
  * `max_iterations::Int`: The maximum number of iterations to execute (default is 100).
  * `min_radius::Float64`: The minimum allowed hyperrectangle radius for further subdivision (default is 1e-5).

# Returns

  * A vector of `DirectRectangle` instances representing the final set of hyperrectangular intervals after the specified number of iterations. Each `DirectRectangle` contains:

      * `c`: the center point (in the unit hypercube),
      * `y`: the objective function value at the center,
      * `d`: the division count per dimension,
      * `r`: the computed radius of the rectangle.
