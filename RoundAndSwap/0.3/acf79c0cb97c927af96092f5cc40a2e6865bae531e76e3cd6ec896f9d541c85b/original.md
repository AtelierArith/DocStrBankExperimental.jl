```
make_models(model::Model, optimizer::Union{Nothing, DataType} = nothing)
```

Given a single model, make enough models to have one for each thread

# Arguments:

  * `optimizer`: Optimizer to use, if nothing, will use the same as the one in the provided model, proving it is one of [Gurobi, Ipopt, HiGHS]
