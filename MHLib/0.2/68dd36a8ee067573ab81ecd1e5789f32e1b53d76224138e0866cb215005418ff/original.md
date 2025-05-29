```
two_exchange_random_fill_neighborhood_search!(::SubsetVectorSolution, best_improvement)
```

Search 2-exchange neighborhood followed by `fillup!()` with random ordering.

Each selected location is tried to be exchanged with each unselected one followed by a `fillup!()`.

The neighborhood is searched in a randomized fashion. Overload the methods `element_removed_delta_eval` and `element_added_delta_eval` for an efficient problem-specific delta evaluation. Returns true if the solution could be improved, otherwise the solution remains unchanged.
