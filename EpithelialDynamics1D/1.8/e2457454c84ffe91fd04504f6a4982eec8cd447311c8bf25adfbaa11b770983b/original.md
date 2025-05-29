```
cell_numbers(sol::EnsembleSolution; indices = eachindex(sol), alpha=0.05)
```

Computes summary statistics for the cell numbers from an `EnsembleSolution` to a [`CellProblem`](@ref).

# Arguments

  * `sol::EnsembleSolution`: The ensemble solution to a `CellProblem`.

# Keyword Arguments

  * `indices = eachindex(sol)`: The indices of the cell simulations to consider.
  * `alpha::Float64 = 0.05`: The significance level for the confidence intervals.

# Outputs

  * `N::Vector{Vector{Int}}`: The cell numbers for each cell simulation.
  * `means::Vector{Float64}`: The mean cell numbers for each cell simulation.
  * `lowers::Vector{Float64}`: The lower bounds of the confidence intervals for the cell numbers for each cell simulation.
  * `uppers::Vector{Float64}`: The upper bounds of the confidence intervals for the cell numbers for each cell simulation.
