```
remove_some!(::SubsetVectorSolution, k)
```

Removes `min(k,sel)` randomly selected elements from the solution.

Uses `element_removed_delta_eval`, which should be overloaded and adapted to the problem. The elements are removed even when the solution becomes infeasible.
