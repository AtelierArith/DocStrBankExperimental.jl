```
fit(model::AbstractTimescaleModel, param_dict=nothing)
```

Fit the timescale model using the specified fitting method.

# Arguments

  * `model`: The timescale model instance to fit
  * `param_dict`: Optional dictionary of fitting parameters. If not provided, default parameters will be used.

# Returns

For ADVI fitting method:

  * `samples`: Array of posterior samples
  * `map_estimate`: Maximum a posteriori estimate of parameters
  * `vi_result`: Full variational inference result object

For ABC fitting method:

  * `samples`: Array of accepted parameter samples
  * `weights`: Importance weights for the samples
  * `distances`: Distances between simulated and observed summary statistics
