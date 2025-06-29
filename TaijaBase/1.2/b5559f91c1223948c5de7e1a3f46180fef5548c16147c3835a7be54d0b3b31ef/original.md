```
parallelize(
    parallelizer::nothing,
    f::Function,
    args...;
    kwargs...,
)
```

If no `AbstractParallelizer` has been supplied, just call or broadcast the function. 

## Note for developers

This function is owned by the `TaijaBase` module to allow shipping it to packages that depend on `TaijaBase`, without having to depend on the `TaijaParallel` module. For example, in `CounterfactualExplanations` we rely on this function to parallelize the computation of counterfactual explanations. Unless the user explicitly provides a parallelizer, the function will just call the function `f` or broadcast it over the collection of arguments. There is no need to depend on `TaijaParallel` for this simple operation.
