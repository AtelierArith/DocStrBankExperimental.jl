```
plot(d::SSM1D; t_range=default_range(d), kwargs...)
```

Plots the probability density of a single alternative sequential sampling model.

# Arguments

  * `d::SSM1D`: a model object for a single alternative sequential sampling model

# Keywords

  * `t_range`: the range of time points over which the probability density is plotted
  * `m_args=()`: optional positional arguments passed to `rand` if applicable
  * `kwargs...`: optional keyword arguments for configuring plot options
