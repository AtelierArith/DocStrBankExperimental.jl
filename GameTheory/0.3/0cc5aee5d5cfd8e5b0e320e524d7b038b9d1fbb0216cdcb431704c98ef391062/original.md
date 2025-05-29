```
payoff_profile_array(g)
```

Return an N-dimensional array of vectors, whose (a_1, ..., a_N)-entry contains a vector of N payoff values, one for each player, for the action profile (a_1, ..., a_N).

# Arguments

  * `g::NormalFormGame` : N-player `NormalFormGame` instance.

# Returns

  * `::Array{Vector,N}` : Array of payoff profiles.
