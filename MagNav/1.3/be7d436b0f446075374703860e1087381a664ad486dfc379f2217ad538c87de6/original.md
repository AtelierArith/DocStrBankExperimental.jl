```
get_autocor(x::Vector, dt = 0.1, dt_max = 300.0)
```

Get autocorrelation of data (e.g., actual - expected measurements).

**Arguments:**

  * `x`:      data vector
  * `dt`:     (optional) measurement time step [s]
  * `dt_max`: (optional) maximum time step to evaluate [s]

**Returns:**

  * `sigma`: standard deviation
  * `tau`:   autocorrelation decay to e^-1 of `x` [s]
