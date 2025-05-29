```
get_next(ctmc::CTMC, t::AbstractFloat)
```

Get the next state transition after a specific time point.

# Arguments

  * `ctmc::CTMC`: The CTMC to query
  * `t::AbstractFloat`: Current time point

# Returns

  * `Tuple{Int,AbstractFloat}`: (next*state, transition*time)

# Note

Returns the next state that will be entered and when it will be entered, searching from the current time point forward.
