```
run_path_sim(CH::AbstractChart; maxiter)
run_path_sim(CH::MultipleControlChart; maxiter)
```

Simulates a run length path for the control chart `CH` by sampling new data from its Phase II object.

### Inputs

  * `CH::AbstractChart` - A control chart.
  * `maxiter::Real` - The maximum value of the run length. Defaults to `min(maxrl(CH), 10*get_nominal_value(CH))`

### Returns

  * A vector containing the simulated values of the control chart.
