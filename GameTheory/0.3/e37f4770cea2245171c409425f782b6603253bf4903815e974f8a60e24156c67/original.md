```
payoff_vector(player, opponent_action)
```

Return a vector of payoff values for a Player in a 2-player game, one for each own action, given the opponent's pure action.

# Arguments

  * `player::Player{2}` : Player instance.
  * `opponent_action::PureAction` : Opponent's pure action (integer).

# Returns

  * `::Vector` : Payoff vector.
