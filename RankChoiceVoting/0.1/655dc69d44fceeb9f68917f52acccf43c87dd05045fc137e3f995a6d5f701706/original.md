```
satisfies(system::VotingSystem, criterion::ReversalSymmetry, rankings::Ranks; _...)
```

Tests whether a voting system satisfies the reversal symmetry criterion.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::ReversalSymmetry`: condorcet criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
