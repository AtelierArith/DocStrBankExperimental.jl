```
is_nash(g, action_profile; tol=1e-8)
```

Return true if `action_profile` is a Nash equilibrium.

# Arguments

  * `g::NormalFormGame` : Instance of N-player NormalFormGame.
  * `action_profile::ActionProfile` : Tuple of N integers (pure actions) or N vectors of reals (mixed actions).
  * `tol::Real` : Tolerance to be used to determine best response actions.

# Returns

  * `::Bool`
