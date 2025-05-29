```
run_sim_sa(CH::AbstractChart, maxiter::Real, delta::Real)
```

Simulates a run length for the control chart `CH` by sampling new data from the Phase II object, to be used by the stochastic approximation algorithm implemented in the `saCL!` function.

### Inputs

  * `CH` - A control chart.
  * `maxiter` - The maximum value of the run length.
  * `delta` - A value controlling how much the control limit must be shifted for the gain estimation during the first stage.

### Returns

  * A `NamedTuple` containing the simulated run length, `rl`, the simulated run length with control limit shifted by `delta`, `rlPlus`, and the simulated run length with control limit shifted by `-delta`, `rlMinus`.
