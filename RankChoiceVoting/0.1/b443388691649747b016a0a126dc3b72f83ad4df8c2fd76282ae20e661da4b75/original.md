```
count_violations(system::VotingSystem, criterion::MutualMajority, rankings::Ranks; _...)
```

Counts the number of violations of the majority criterion for a given voting system. The count is either 0 or 1.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::Majority`: majority criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
