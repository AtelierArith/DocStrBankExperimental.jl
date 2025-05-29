```
count_violations(system::VotingSystem, criterion::Consistency, rankings::Ranks; n_reps=1000, _...)
```

Uses Monte Carlo simulation to count the number of violations of the consistency criterion for a given voting system.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::Consistency`: condorcet criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks

# Keywords

  * `n_reps`: number of Monte Carlo simulations to perform
