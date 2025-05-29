```
histogram!([cur_plot], d::ContinuousMultivariateSSM;  kwargs...)
```

Adds histogram of a multi-alternative sequential sampling model to an existing plot

# Arguments

  * `cur_plot`: optional current plot
  * `d::SSM2D`: a model object for a mult-alternative sequential sampling model

# Keywords

  * `norm=true`: histogram scaled according to density if true
  * `m_args=()`: optional positional arguments passed to `rand`
  * `n_sim=2000`: the number of data points used in the histogram
  * `kwargs...`: optional keyword arguments for configuring  plot options
