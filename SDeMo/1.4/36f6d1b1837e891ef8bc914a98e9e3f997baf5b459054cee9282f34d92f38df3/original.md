```
explain(model::AbstractSDM, j; observation = nothing, instances = nothing, samples = 100, kwargs..., )
```

Uses the MCMC approximation of Shapley values to provide explanations to specific predictions. The second argument `j` is the variable for which the explanation should be provided.

The `observation` keywords is a row in the `instances` dataset for which explanations must be provided. If `instances` is `nothing`, the explanations will be given on the training data.

All other keyword arguments are passed to `predict`.
