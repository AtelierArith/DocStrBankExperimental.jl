```
satisfies(system::VotingSystem, criterion::CondorcetWinner, rankings::Ranks; _...)
```

Tests whether a voting system satisfies the Condorcet winner criterion.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::CondorcetWinner`: condorcet criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
