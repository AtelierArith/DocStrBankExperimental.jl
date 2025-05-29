```
optimize_grid(CH::ControlChart, rlconstr::Function, settings::OptSettings)
```

Optimizes a control chart by finding the best set of parameters using a grid search.

### Arguments

  * `CH::ControlChart`: The control chart object whose parameters must be optimized.
  * `rlconstr::Functiom`: The function that evaluates the OC performance of the control chart.
  * `settings::OptSettings`: The optimization settings.

### Returns

  * par_current (Vector{Float64}): the optimal set of parameters found by the optimization algorithm.

### References

Qiu, P. (2008). Distribution-Free Multivariate Process Control Based on Log-Linear Modeling. IIE Transactions, 40(7), 664-677. https://doi.org/10.1080/07408170701744843
