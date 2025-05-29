```
has_consistent_distributions(m::MDP; atol=0)
has_consistent_distributions(m::POMDP; atol=0)
```

Return true if no problems are found in the distributions for a discrete problem. Print information and return false if problems are found.

Tests whether

  * All probabilities are positive
  * Probabilities for all distributions sum to 1
  * All items with positive probability are in the support

# Keyword Arguments

  * `atol`: absolute tolerance passed to `approx` for all probability checks
