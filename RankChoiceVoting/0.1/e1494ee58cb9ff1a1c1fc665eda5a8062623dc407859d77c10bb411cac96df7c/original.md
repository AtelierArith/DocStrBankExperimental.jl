```
satisfies(::Fails, system::VotingSystem, criteria::Monotonicity, rankings::Ranks; n_reps=1000, _...)
```

Uses Monte Carlo simulation to tests whether a voting system satisfies the monotonicity criterion.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criteria::Monotonicity`: monotonicity criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks

# Keywords

  * `n_reps=1000`: maximum number of Monte Carlo simulations to perform while searching

for a violation
