```
plot(d::ContinuousMultivariateSSM; t_range=default_range(d), kwargs...)
```

Plots the marginal probability density of each N dimensional continuous sequential samping model.

# Arguments

  * `d::ContinuousMultivariateSSM`: a model object for a N dimensional continuous sequential samping model.

# Keywords

  * `t_range`: the range of time points over which the probability density is plotted
  * `m_args=()`: optional positional arguments passed to `rand` if applicable
  * `kwargs...`: optional keyword arguments for configuring plot options
