```
satisfies(system::VotingSystem, criterion::CondorcetLoser, rankings::Ranks; _...)
```

Tests whether a voting system satisfies the Condorcet loser criterion.

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::CondorcetLoser`: condorcet loser criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
