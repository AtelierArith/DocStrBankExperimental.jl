```
swap(model::Model, consider_swapping::Array{VariableRef}; optimizer = nothing, max_swaps = Inf,save_path::Union{Nothing, String}=nothing)
```

Given a model and a list of variables swap the integer values to improve the objective function

# Arguments:

  * `models`: An array of models, one for each thread
  * `consider_swapping`: An array of variables to consider swapping
  * `optimizer`: A specific optimizer to use, if the desired is not in [Gurobi, Ipopt, HiGHS]
  * `max_swaps`: The maximum number of swaps, default is Inf
  * `save_path`: A path to save the swapper to after each swap, isnothing(save_path) ?  don't save : save, default is nothing
