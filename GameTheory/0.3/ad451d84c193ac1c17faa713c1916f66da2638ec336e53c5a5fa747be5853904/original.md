```
is_nash(g, action; tol=1e-8)
```

Return true if `action` is a Nash equilibrium of a trivial game with 1 player.

# Arguments

  * `g::NormalFormGame{1}` : Instance of 1-player NormalFormGame.
  * `action::Action` : Integer (pure action) or vector of reals (mixed action).
  * `tol::Float64` : Tolerance to be used to determine best response actions.

# Returns

  * `::Bool`
