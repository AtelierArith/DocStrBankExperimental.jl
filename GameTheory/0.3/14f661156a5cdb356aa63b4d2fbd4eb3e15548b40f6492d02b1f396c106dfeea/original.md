```
play!(rng, ld, player_ind, actions)
```

Return a new action of player indexed by `player_ind` given each players' choice probabilities.

# Arguments

  * `rng::AbstractRNG` : Random number generator used.
  * `ld::LogitDynamics{N}` : `LogitDynamics` instance.
  * `player_ind::Integer` : A player index who takes an action.
  * `actions::Vector{<:Integer}` : The action profile.

# Returns

  * `::Integer` : The new action of the player indexed by `player_ind`.
