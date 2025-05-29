```
satisfies(system::VotingSystem, criterion::MutualMajority, rankings::Ranks; _...)
```

Tests whether a voting system satisfies the mutual majority criterion.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::MutualMajority`: majority criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
