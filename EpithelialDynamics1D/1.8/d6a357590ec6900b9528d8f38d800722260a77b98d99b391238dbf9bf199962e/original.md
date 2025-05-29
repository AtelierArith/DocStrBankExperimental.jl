```
node_densities(sol::EnsembleSolution;
    indices=eachindex(sol),
    num_knots=500,
    stat=(minimum, maximum),
    knots=get_knots(sol, num_knots; indices, stat),
    alpha=0.05,
    interp_fnc=(u, t) -> LinearInterpolation{true}(u, t),
    smooth_boundary=true)
```

Computes summary statistics for the node densities from an `EnsembleSolution` to a [`CellProblem`](@ref). Any  negative values are set to zero.

# Arguments

  * `sol::EnsembleSolution`: The ensemble solution to a `CellProblem`.

# Keyword Arguments

  * `indices = eachindex(sol)`: The indices of the cell simulations to consider.
  * `num_knots::Int = 500`: The number of knots to use for the spline interpolation.
  * `stat = (minimum, maximum)`: How to summarise the knots for `get_knots`.
  * `parallel = false`: Whether to use multithreading for the loops.
  * `knots::Vector{Vector{Float64}} = get_knots(sol, num_knots; indices, stat, parallel)`: The knots to use for the spline interpolation.
  * `alpha::Float64 = 0.05`: The significance level for the confidence intervals.
  * `interp_fnc = (u, t) -> LinearInterpolation{true}(u, t)`: The function to use for constructing the interpolant.
  * `smooth_boundary::Bool = true`: Whether to use the smooth boundary node densities.
  * `extrapolate = false`: Whether to allow for extrapolation when considering evaluating outside the range of cells for a given time and a given simulation.

# Outputs

  * `q::Vector{Vector{Vector{Float64}}}`: The node densities for each cell simulation.
  * `r::Vector{Vector{Vector{Float64}}}`: The cell positions for each cell simulation.
  * `means::Vector{Vector{Float64}}`: The mean node densities for each cell simulation.
  * `lowers::Vector{Vector{Float64}}`: The lower bounds of the confidence intervals for the node densities for each cell simulation.
  * `uppers::Vector{Vector{Float64}}`: The upper bounds of the confidence intervals for the node densities for each cell simulation.
  * `knots::Vector{Vector{Float64}}`: The knots used for the spline interpolation.
