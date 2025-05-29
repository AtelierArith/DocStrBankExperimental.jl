```
is_best_response(player, own_action, opponents_actions; tol=1e-8)
```

Return true if `own_action` is a best response to `opponents_actions`.

# Arguments

  * `player::Player` : Player instance.
  * `own_action::MixedAction` : Own mixed action (vector of reals).
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : Profile of N-1 opponents' actions. If N=2, then it must be a vector of reals (in which case it is treated as the opponent's mixed action) or a scalar of integer (in which case it is treated as the opponent's pure action). If N>2, then it must be a tuple of N-1 integers (pure actions) or N-1 vectors of reals (mixed actions). (For the degenerate case N=1, it must be `nothing`.)
  * `tol::Real` : Tolerance to be used to determine best response actions.

# Returns

  * `::Bool` : True if `own_action` is a best response to `opponents_actions`; false otherwise.
