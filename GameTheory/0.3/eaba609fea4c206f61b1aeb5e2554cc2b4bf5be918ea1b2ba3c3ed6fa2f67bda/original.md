```
best_responses(player, opponents_actions; tol=1e-8)
```

Return all the best response actions to `opponents_actions`.

# Arguments

  * `player::Player` : Player instance.
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : Profile of N-1 opponents' actions. If N=2, then it must be a vector of reals (in which case it is treated as the opponent's mixed action) or a scalar of integer (in which case it is treated as the opponent's pure action). If N>2, then it must be a tuple of N-1 integers (pure actions) or N-1 vectors of reals (mixed actions). (For the degenerate case N=1, it must be `nothing`.)
  * `tol::Real` : Tolerance to be used to determine best response actions.

# Returns

  * `best_responses::Vector{Int}` : Vector containing all the best response actions.
