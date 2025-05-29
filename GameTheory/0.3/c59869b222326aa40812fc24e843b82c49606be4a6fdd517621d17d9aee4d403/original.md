```
payoff_vector(player, opponents_actions)
```

Return a vector of payoff values for a Player in an N>2 player game, one for each own action, given a tuple of the opponents' mixed actions.

# Arguments

  * `player::Player` : Player instance.
  * `opponents_actions::MixedActionProfile` : Tuple of N-1 opponents' mixed actions.

# Returns

  * `::Vector` : Payoff vector.
