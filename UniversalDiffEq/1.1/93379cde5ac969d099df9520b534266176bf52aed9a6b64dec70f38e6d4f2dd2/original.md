```
MultiNODE(data;kwargs...)
```

builds a NODE model to fit to the data. `data` is a DataFrame object with time arguments placed in a column labed `t` and a second column with a unique index for each time series. The remaining columns have observations of the state variables at each point in time and for each time series.

# kwargs

  * `time_column_name`: Name of column in `data` that corresponds to time. Default is `"time"`.
  * `series_column_name`: Name of column in `data` that corresponds to series. Default is `"series"`.
  * `hidden_units`: Number of neurons in hidden layer. Default is `10`.
  * `seed`: Fixed random seed for repeatable results. Default is `1`.
  * `proc_weight`: Weight of process error `omega_{proc}`. Default is `1.0`.
  * `obs_weight`: Weight of observation error `omega_{obs}`. Default is `1.0`.
  * `reg_weight`: Weight of regularization error `omega_{reg}`. Default is `10^-6`.
  * `reg_type`: Type of regularization, whether `"L1"` or `"L2"` regularization. Default is `"L2"`.
  * `l`: Extrapolation parameter for forecasting. Default is `0.25`.
  * `extrap_rho`: Extrapolation parameter for forecasting. Default is `0.0`.
  * `ode_solver`: method to aproximate solutions to the differntail equation. Defaul is `Tsit5()`.
  * `ad_method`:method to evalaute derivatives of the ODE solver. Default is `ForwardDiffSensitivity()`.
