```
CustomDifference(data,step,initial_parameters;kwrags...)
```

Constructs a UDE model for the data set `data` based on user defined difference equation `step`. An initial guess of model parameters are supplied with the initial_parameters argument. ...

# Arguments

  * data: a DataFrame object with the time of observations in a column labeled `t` and the remaining columns the value of the state variables at each time point.
  * step: a Function of the form `step(u,t,p)` where `u` is the value of the state variables, `p` are the model parameters.
  * init_parameters: A `NamedTuple` with the model parameters. Neural network parameters must be listed under the key `NN`.

# kwargs

  * `time_column_name`: Name of column in `data` that corresponds to time. Default is `"time"`.
  * `proc_weight`: Weight of process error $omega_{proc}$. Default is `1.0`.
  * `obs_weight`: Weight of observation error $omega_{obs}$. Default is `1.0`.
  * `reg_weight`: Weight of regularization error $omega_{reg}$. Default is `10^-6`.
  * `reg_type`: Type of regularization, whether `"L1"` or `"L2"` regularization. Default is `"L2"`.
  * `l`: Extrapolation parameter for forecasting. Default is `0.25`.
  * `extrap_rho`: Extrapolation parameter for forecasting. Default is `0.0`.

...
