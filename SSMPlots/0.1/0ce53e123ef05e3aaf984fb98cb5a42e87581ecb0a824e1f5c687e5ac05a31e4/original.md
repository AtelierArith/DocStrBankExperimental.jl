```
histogram([cur_plot], d::SSM1D; norm=true, n_sim=2000, kwargs...)
```

Adds histogram of a single alternative sequential sampling model to an existing plot

# Arguments

  * `cur_plot`: optional current plot
  * `d::SSM1D`: a model object for a single alternative sequential sampling model

# Keywords

  * `norm=true`: histogram scaled according to density if true
  * `m_args=()`: optional positional arguments passed to `rand`
  * `n_sim=2000`: the number of data points used in the histogram
  * `kwargs...`: optional keyword arguments for configuring  plot options
