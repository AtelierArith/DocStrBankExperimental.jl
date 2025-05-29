```
KMR(N, payoff_array, epsilon)
```

Create a new KMR instance.

# Arguments

  * `N::Integer` : The number of players.
  * `payoff_array::Matrix` : The payoff array for each player.
  * `epsilon::Float64` : The probability of strategy flips.

# Returns

  * `::KMR` : The Kandori Mailath Rob model.
