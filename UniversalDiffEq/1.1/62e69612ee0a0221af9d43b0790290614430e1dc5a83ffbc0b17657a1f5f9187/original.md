```
NODE(data,X;kwargs ... )
```

When a data frame `X` is supplied the model will run with covariates. The argument `X` should have a column for time `t` with the value for time in the remaining columns. The values in `X` will be interpolated with a linear spline for values of time not included in the data frame.

  * `time_column_name`: Name of column in `data` and `X` that corresponds to time. Default is `"time"`.
  * `variable_column_name`: Name of column in `X` that corresponds to the variables. Default is `nothing`.
  * `value_column_name`: Name of column in `X` that corresponds to the covariates. Default is `nothing`.
  * `hidden_units`: Number of neurons in hidden layer. Default is `10`.
  * `seed`: Fixed random seed for repeatable results. Default is `1`.
  * `proc_weight`: Weight of process error $omega_{proc}$. Default is `1.0`.
  * `obs_weight`: Weight of observation error $omega_{obs}$. Default is `1.0`.
  * `reg_weight`: Weight of regularization error $omega_{reg}$. Default is `10^-6`.
  * `reg_type`: Type of regularization, whether `"L1"` or `"L2"` regularization. Default is `"L2"`.
  * `l`: Extrapolation parameter for forecasting. Default is `0.25`.
  * `extrap_rho`: Extrapolation parameter for forecasting. Default is `0.0`.
  * `ode_solver`: method to aproximate solutions to the differntail equation. Defaul is `Tsit5()`.
  * `ad_method`:method to evalaute derivatives of the ODE solver. Default is `ForwardDiffSensitivity()`.
