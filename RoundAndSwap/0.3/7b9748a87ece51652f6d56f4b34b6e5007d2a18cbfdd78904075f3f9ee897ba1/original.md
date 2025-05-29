```
swap(models::Array{Model}, consider_swapping::Array{VariableRef}; max_swaps = Inf, optimizer = nothing)
```

Given a model and a list of variables swap the integer values to improve the objective function

# Arguments:

  * `models`: An array of models, one for each thread
  * `consider_swapping`: An array of variables to consider swapping
  * `max_swaps`: The maximum number of swaps, default is Inf
  * `save_path`: A path to save the swapper to after each swap, isnothing(save_path) ?  don't save : save, default is nothing
  * `auto_cpu_limit`: Whether to set a cpu time limie. Once enough feasible and infeasible solutions have been determined if there is sufficient gap in the solve time between the two this will be used to set the cpu time limit.
