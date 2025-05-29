```
leading_edges(sol::EnsembleSolution; indices = eachindex(sol), alpha=0.05)
```

Computes summary statistics for the leading edges from an `EnsembleSolution` to a [`CellProblem`](@ref).

# Arguments

  * `sol::EnsembleSolution`: The ensemble solution to a `CellProblem`.

# Keyword Arguments

  * `indices = eachindex(sol)`: The indices of the cell simulations to consider.
  * `alpha::Float64 = 0.05`: The significance level for the confidence intervals.

# Outputs

  * `L::Vector{Vector{Float64}}`: The leading edges for each cell simulation.
  * `means::Vector{Float64}`: The mean leading edges for each cell simulation.
  * `lowers::Vector{Float64}`: The lower bounds of the confidence intervals for the leading edges for each cell simulation.
  * `uppers::Vector{Float64}`: The upper bounds of the confidence intervals for the leading edges for each cell simulation.
