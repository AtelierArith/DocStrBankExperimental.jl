```
CustomDifference(data::DataFrame,step,initial_parameters,priors::Function;kwargs ... )
```

When a function's priors is supplied its value will be added to the loss function as a penalty term for user-specified parameters. It should take the a single NamedTuple `p` as an argument penalties for each parameter should be calcualted by accessing `p` with the period operator.

```julia
function priors(p)
    l = 0.01*(p.r - 1.5)^2
    l += 0.01*(p.beta)^2
    return l
end
```

# kwargs

  * `time_column_name`: Name of column in `data` that corresponds to time. Default is `"time"`.
  * `proc_weight`: Weight of process error $omega_{proc}$. Default is `1.0`.
  * `obs_weight`: Weight of observation error $omega_{obs}$. Default is `1.0`.
  * `reg_weight`: Weight of regularization error $omega_{reg}$. Default is `10^-6`.
  * `reg_type`: Type of regularization, whether `"L1"` or `"L2"` regularization. Default is `"L2"`.
  * `l`: Extrapolation parameter for forecasting. Default is `0.25`.
  * `extrap_rho`: Extrapolation parameter for forecasting. Default is `0.0`.
