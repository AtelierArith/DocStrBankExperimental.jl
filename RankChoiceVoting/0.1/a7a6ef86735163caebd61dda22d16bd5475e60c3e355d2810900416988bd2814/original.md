```
count_violations(system::VotingSystem, criteria::Monotonicity, rankings::Ranks; n_reps=1000, _...)
```

Uses Monte Carlo simulation to counts the number of violations of the monotonicity criterion for a given voting system.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criteria::Monotonicity`: condorcet criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks

# Keywords

  * `n_reps=1000`: maximum number of Monte Carlo simulations to perform
