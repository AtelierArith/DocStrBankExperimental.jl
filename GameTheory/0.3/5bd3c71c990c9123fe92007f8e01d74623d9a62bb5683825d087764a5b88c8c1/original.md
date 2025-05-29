```
LogitDynamics{N, T, S}
```

Type representing the Logit-Dynamics model.

# Fields

  * `players::NTuple{N,Player{N,T}}` : Tuple of `Player` instances.
  * `nums_actions::NTuple{N,Int}` : Tuple of the numbers of actions, one for each player.
  * `beta<:Real` : The level of noise in a player's decision.
  * `choice_probs::Vector{Array}` : The choice probabilities of each action, one for each player.
