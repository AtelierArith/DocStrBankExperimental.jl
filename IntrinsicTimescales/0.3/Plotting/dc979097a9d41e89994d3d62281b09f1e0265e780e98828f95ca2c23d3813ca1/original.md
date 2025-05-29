```
plot(container::ABCResults, model::Models.AbstractTimescaleModel; show::Bool=true)
```

Plot posterior predictive check for ABC results. Shows the data summary statistics (ACF or PSD) with posterior predictive samples overlaid.

# Arguments

  * `container::ABCResults`: Container with ABC results
  * `model::Models.AbstractTimescaleModel`: Model used for inference
  * `show::Bool=true`: Whether to display the plot
  * `n_samples::Int=100`: Number of posterior samples to use for prediction

# Returns

  * Plot object
