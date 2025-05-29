```
grid_search(prob; save_vals=Val(false), minimise:=Val(false), parallel=Val(false))
```

Performs a grid search for the given grid search problem `prob`.

# Arguments

  * `prob::GridSearch{F, G}`: The grid search problem.

# Keyword Arguments

  * `save_vals:=Val(false)`: Whether to return a array with the function values.
  * `minimise:=Val(false)`: Whether to minimise or to maximise the function.
  * `parallel:=Val(false)`: Whether to run the grid search with multithreading.

# Outputs

  * `f_opt`: The optimal objective value.
  * `x_argopt`: The parameter that gave `f_opt`.
  * `f_res`: If `save_vals==Val(true)`, then this is the array of function values.
