```
plot_model(model; 
    add_density=false, density_kwargs=(), n_sim=1, kwargs...)
```

Plot the evidence accumulation process of a continous multivariate sequential sampling model.

# Arguments

  * `model::ContinuousMultivariateSSM`: a continous multivariate sequential sampling model

# Keywords

  * `add_density=false`: add density plot above threshold line if true
  * `density_kwargs=()`: pass optional keyword arguments to density plot
  * `labels = default_labels(model)`: a vector of parameter label options
  * `n_sim=1`: the number of simulated decision processes per option
  * `kwargs...`: optional keyword arguments for configuring plot options
