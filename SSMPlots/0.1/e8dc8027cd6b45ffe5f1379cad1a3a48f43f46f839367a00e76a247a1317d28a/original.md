```
plot!([cur_plot], d::ContinuousMultivariateSSM; t_range=default_range(d), kwargs...)
```

Adds the marginal probability density of a multivariate continuous sequential sampling model to an existing plot

# Arguments

  * `cur_plot`: optional current plot
  * `d::ContinuousMultivariateSSM`: a multivariate continuous sequential sampling model

# Keywords

  * `t_range`: the range of time points over which the probability density is plotted
  * `m_args=()`: optional positional arguments passed to `rand` if applicable
  * `kwargs...`: optional keyword arguments for configuring plot options
