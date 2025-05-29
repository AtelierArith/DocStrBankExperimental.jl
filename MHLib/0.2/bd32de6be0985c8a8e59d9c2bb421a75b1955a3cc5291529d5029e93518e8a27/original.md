```
two_opt_neighborhood_search(::PermutationSolution, best_improvement)
```

Systematic search of the 2-opt neighborhood, i.e., consider all inversions of subsequences.

The neighborhood is searched in a randomized ordering. Boolean Parameter best_improvement  defines whether best improvement or next improvement step functions is used. Returns true  if a better solution has been found.
