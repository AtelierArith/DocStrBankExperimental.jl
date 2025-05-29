```
best_response([rng=GLOBAL_RNG], player, opponents_actions;
              tie_breaking=:smallest, tol=1e-8)
```

Return a best response action to `opponents_actions`.

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG` : Random number generator; relevant only with `tie_breaking=:random`.
  * `player::Player` : Player instance.
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : Profile of N-1 opponents' actions. If N=2, then it must be a vector of reals (in which case it is treated as the opponent's mixed action) or a scalar of integer (in which case it is treated as the opponent's pure action). If N>2, then it must be a tuple of N-1 integers (pure actions) or N-1 vectors of reals (mixed actions). (For the degenerate case N=1, it must be `nothing`.)
  * `tie_breaking::Symbol` : Control how to break a tie (see Returns for details).
  * `tol::Real` : Tolerance to be used to determine best response actions.

# Returns

  * `::Int` : If `tie_breaking=:smallest`, returns the best response action with the smallest index; if `tie_breaking=:random`, returns an action randomly chosen from the best response actions.
