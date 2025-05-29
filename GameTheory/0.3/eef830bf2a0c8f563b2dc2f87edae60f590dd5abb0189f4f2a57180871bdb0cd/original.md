```
payoff_vector(player, opponents_actions)
```

Return a vector of payoff values for a Player in an N>2 player game, one for each own action, given a tuple of the opponents' pure actions.

# Arguments

  * `player::Player` : Player instance.
  * `opponents_actions::PureActionProfile` : Tuple of N-1 opponents' pure actions.

# Returns

  * `::Vector` : Payoff vector.
