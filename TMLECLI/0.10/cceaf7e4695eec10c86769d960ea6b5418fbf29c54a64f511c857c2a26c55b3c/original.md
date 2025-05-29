```
GLMNetRegressor(;resampling=CV(), params...)
```

A GLMNet regressor for continuous outcomes based on the `glmnetcv` function from the [GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl)  package.

# Arguments:

  * resampling: A MLJ `ResamplingStrategy`, see [MLJ resampling strategies](https://alan-turing-institute.github.io/MLJ.jl/dev/evaluating_model_performance/#Built-in-resampling-strategies)
  * params: Additional parameters to the `glmnetcv` function

# Examples:

A glmnet with `alpha=0`.

```julia

model = GLMNetRegressor(resampling=CV(nfolds=3), alpha=0)
mach = machine(model, X, y)
fit!(mach, verbosity=0)
```
