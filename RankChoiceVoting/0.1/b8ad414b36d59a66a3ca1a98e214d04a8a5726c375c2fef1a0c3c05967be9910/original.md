```
count_violations(system::VotingSystem, criterion::Majority, rankings::Ranks; _...)
```

Counts the number of violations of the majority criterion for a given voting system.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::Majority`: majority criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
