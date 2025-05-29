```
MultiCustomDerivatives(data,derivs!,initial_parameters;kwargs...)
```

Builds a UDE model that can be trianed on multiple time series simultaniously. The user defined derivatives functions must allow for an extra argument `i` that indexes over the time series in the data set (e.g. `derivs!(du,u,i,)`). `data` is a DataFrame object with time arguments placed in a column labeled `t` and a second column with a unique index for each time series. The remaining columns have observations of the state variables at each point in time and for each time series.

# kwargs

  * `time_column_name`: Name of column in `data` that corresponds to time. Default is `"time"`.
  * `series_column_name`: Name of column in `data` that corresponds to series. Default is `"series"`.
  * `variable_column_name`: Name of column in `data` that corresponds to the variables. Default is `"variable"`.
  * `value_column_name`: Name of column in `data` that corresponds to the covariates. Default is `"value"`.
  * `proc_weight`: Weight of process error `omega_{proc}`. Default is `1.0`.
  * `obs_weight`: Weight of observation error `omega_{obs}`. Default is `1.0`.
  * `reg_weight`: Weight of regularization error `omega_{reg}`. Default is `10^-6`.
  * `reg_type`: Type of regularization, whether `"L1"` or `"L2"` regularization. Default is `"L2"`.
  * `l`: Extrapolation parameter for forecasting. Default is `0.25`.
  * `extrap_rho`: Extrapolation parameter for forecasting. Default is `0.0`.
  * `ode_solver`: method to aproximate solutions to the differntail equation. Defaul is `Tsit5()`.
  * `ad_method`:method to evalaute derivatives of the ODE solver. Default is `ForwardDiffSensitivity()`.
