```
satisfies(system::VotingSystem, criterion::Consistency, rankings::Ranks; n_max=1000, _...)
```

Uses Monte Carlo simulation to test whether a voting system satisfies the Consistency criterion.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::Consistency`: consistency criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks

# Keywords

  * `n_reps`: maximum Monte Carlo simulations to perform
