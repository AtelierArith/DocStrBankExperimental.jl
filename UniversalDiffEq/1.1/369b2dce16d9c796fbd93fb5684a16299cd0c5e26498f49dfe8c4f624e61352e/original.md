```
EasyNODE(data;kwargs ... )
```

Constructs a pretrained continuous-time model for the data set `data` using a single layer neural network to represent the system's dynamics.

# kwargs

  * `time_column_name`: Name of column in `data` that corresponds to time. Default is `"time"`.
  * `hidden_units`: Number of neurons in hidden layer. Default is `10`.
  * `seed`: Fixed random seed for repeatable results. Default is `1`.
  * `proc_weight`: Weight of process error $omega_{proc}$. Default is `1.0`.
  * `obs_weight`: Weight of observation error $omega_{obs}$. Default is `1.0`.
  * `reg_weight`: Weight of regularization error $omega_{reg}$. Default is `10^-6`.
  * `reg_type`: Type of regularization, whether `"L1"` or `"L2"` regularization. Default is `"L2"`.
  * `l`: Extrapolation parameter for forecasting. Default is `0.25`.
  * `extrap_rho`: Extrapolation parameter for forecasting. Default is `0.0`.
  * `step_size`: Step size for ADAM optimizer. Default is `0.05`.
  * `maxiter`: Maximum number of iterations in gradient descent algorithm. Default is `500`.
  * `verbose`: Should the training loss values be printed?. Default is `false`.
