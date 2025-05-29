```
grid_search(f, grid::AbstractGrid; save_vals=Val(false), minimise=Val(false), parallel=Val(false))
```

For a given `grid` and function `f`, performs a grid search. 

# Arguments

  * `f`: The function to optimise.
  * `grid::AbstractGrid`: The grid to use for optimising.

# Keyword Arguments

  * `save_vals=Val(false)`: Whether to return a array with the function values.
  * `minimise=Val(false)`: Whether to minimise or to maximise the function.
  * `parallel=Val(false)`: Whether to run the grid search with multithreading.
