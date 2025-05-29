```
histogram(d::SSM1D; norm=true, n_sim=2000, kwargs...)
```

Plots the histogram of a single alternative sequential sampling model.

# Arguments

  * `d::SSM1D`: a model object for a single alternative sequential sampling model

# Keywords

  * `norm=true`: histogram scaled according to density if true
  * `m_args=()`: optional positional arguments passed to `rand`
  * `n_sim=2000`: the number of data points used in the histogram
  * `kwargs...`: optional keyword arguments for configuring  plot options
