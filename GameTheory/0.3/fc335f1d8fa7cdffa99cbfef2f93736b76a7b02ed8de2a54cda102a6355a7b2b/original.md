```
random_pure_actions([rng=GLOBAL_RNG], nums_actions)
```

Return a tuple of random pure actions (integers).

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG`: Random number generator used.
  * `nums_actions::NTuple{N,Int}`: N-tuple of the numbers of actions, one for each player.

# Returns

  * `::NTuple{N,Int}`: N-tuple of random pure actions.
