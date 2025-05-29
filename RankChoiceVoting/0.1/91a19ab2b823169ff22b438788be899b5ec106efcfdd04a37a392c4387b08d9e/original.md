```
count_violations(system::VotingSystem, criterion::ReversalSymmetry, rankings::Ranks; _...)
```

Counts the number of violations of the reversal symmetry criterion for a given voting system.  The number of violations is either 0 or 1. 

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::ReversalSymmetry`: reversal symmetry criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
