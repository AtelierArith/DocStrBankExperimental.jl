```
plot_model(model; 
    add_density=false, density_kwargs=(), n_sim=1, kwargs...)
```

Plot the evidence accumulation process of a generic SSM.

# Arguments

  * `model`: a generic object representing an SSM

# Keywords

  * `add_density=false`: add density plot above threshold line if true
  * `density_kwargs=()`: pass optional keyword arguments to density plot
  * `labels = default_labels(model)`: a vector of parameter label options
  * `density_scale = compute_threshold(model)`: scale the maximum height of the density
  * `n_sim=1`: the number of simulated decision processes per option
  * `kwargs...`: optional keyword arguments for configuring plot options
