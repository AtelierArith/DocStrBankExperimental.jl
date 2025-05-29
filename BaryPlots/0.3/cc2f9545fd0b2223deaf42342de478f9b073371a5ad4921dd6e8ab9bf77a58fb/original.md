```
identify_neutral_edges(params::ReplicatorParams; tol::Float64 = 1e-8, samples::Int = 100) -> Vector{Int}
```

Identifies "neutral" edges in the simplex under the given payoff functions. An edge is neutral if, for all sampled points on that edge, the payoffs of the two involved strategies are effectively equal.

# Arguments

  * `params`: A `ReplicatorParams` struct containing the payoff functions and extra parameters.
  * `tol`: Tolerance for payoff difference. If `|wᵢ - wⱼ|` < `tol` across all samples, that edge is considered neutral.
  * `samples`: Number of points to sample along each edge. Default is `100`.

# Returns

  * A vector of edge indices `{1,2,3}`, each corresponding to:

      * `1`: Edge between Strategy 1 and Strategy 2
      * `2`: Edge between Strategy 2 and Strategy 3
      * `3`: Edge between Strategy 3 and Strategy 1

# Notes

  * This function is used inside `plot_evolution` to highlight edges where the game exhibits neutral stability.
