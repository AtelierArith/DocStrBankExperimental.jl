```
satisfies(::Fails, system::VotingSystem, criterion::IIA, rankings::Ranks;  _...)
```

Tests whether a voting system satisfies the IIA of Irrelevant alternatives criterion. There are several ways to test this criterion. Currently, it is tested by removing subsets of losing candidates and  testing whether the winner changes. The function checks all possible combinations of subsets until the  first violation is encountered. Other methods could add and/or subtract candidates and test whether the  rank order changes. The current method is less strict compared to alternative methods. 

# Arguments

  * `system::VotingSystem`: a voting system object
  * `criterion::IIA`: IIA criterion object
  * `rankings::Ranks`: a rank choice voting object consisting of rank counts and unique ranks
