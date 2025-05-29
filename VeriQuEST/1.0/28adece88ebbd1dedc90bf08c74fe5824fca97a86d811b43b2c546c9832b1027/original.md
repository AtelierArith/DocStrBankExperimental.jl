```
draw_random_rounds(total_rounds, computation_rounds)
```

Generates a random sequence of computation and test rounds. The function first calculates the number of test rounds by subtracting the number of computation rounds from the total rounds. It then creates arrays of `ComputationRound` and `TestRound` instances, and returns a shuffled concatenation of these arrays.

# Arguments

  * `total_rounds`: The total number of rounds.
  * `computation_rounds`: The number of computation rounds.

# Returns

  * `Array`: A shuffled array of `ComputationRound` and `TestRound` instances.

# Examples

```julia
total_rounds = 10
computation_rounds = 5
rounds = draw_random_rounds(total_rounds, computation_rounds)
```
