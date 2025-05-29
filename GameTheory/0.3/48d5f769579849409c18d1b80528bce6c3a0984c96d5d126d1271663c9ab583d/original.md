```
payoff_vector(player, opponent_action)
```

Return a vector of payoff values for a Player in a 2-player game, one for each own action, given the opponent's mixed action.

# Arguments

  * `player::Player{2}` : Player instance.
  * `opponent_action::MixedAction` : Opponent's mixed action (vector of reals).

# Returns

  * `::Vector` : Payoff vector.
