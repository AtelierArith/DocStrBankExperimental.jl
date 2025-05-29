```
Game(; rewards, num_rounds, num_players=length(size(rewards(1))), show_rounds_left=true)
```

Constructs a game of type `Game`. Warning: Developers are not sure the infrastructure will work if the following assumption does not hold:

  * Indexes are symmetric (action `i` of player `s` is the same as action `i` of player `k` ∀i,s,k).

Arguments:

  * `rewards::Function`: Function that returns the reward of each round (`rewards(round) -> Array{Float64, num_players}`);
  * `num_rounds::Int`: Number of rounds in the game;
  * `num_players::Int` Number of players in the game;
  * `show_rounds_left::Bool`: If set, game will disclose how many rounds are left each round.
