```
grid_search(prob::LikelihoodProblem, grid::AbstractGrid, parallel=Val(false); save_vals=Val(false))
```

Given a `grid` and a likelihood problem `prob`, maximises it over the grid using a grid search. If  `save_vals==Val(true)`, then the likelihood function values at each gridpoint are returned. Set  `parallel=Val(true)` if you want multithreading.
