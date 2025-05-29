```
best_response(player, opponents_actions, payoff_perturbation)
```

Return the perturbed best response to `opponents_actions`.

# Arguments

  * `player::Player` : Player instance.
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : Profile of N-1 opponents' actions. If N=2, then it must be a vector of reals (in which case it is treated as the opponent's mixed action) or a scalar of integer (in which case it is treated as the opponent's pure action). If N>2, then it must be a tuple of N-1 integers (pure actions) or N-1 vectors of reals (mixed actions). (For the degenerate case N=1, it must be `nothing`.)
  * `payoff_perturbation::Vector{Float64}` : Vector of length equal to the number of actions of the player containing the values ("noises") to be added to the payoffs in determining the best response.

# Returns

  * `::Int` : Best response action.
