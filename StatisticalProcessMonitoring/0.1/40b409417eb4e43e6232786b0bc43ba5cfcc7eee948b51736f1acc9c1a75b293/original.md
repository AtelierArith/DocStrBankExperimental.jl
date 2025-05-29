```
run_sim_oc(CH::AbstractChart; shift = 0.0)
```

Simulates a run length under location shift for the control chart `CH` by sampling new data from its Phase II object.

### Inputs

  * `CH::AbstractChart`:  A control chart.
  * `shift::Float64` - The magnitude of location shift.

### Returns

  * An `Int` representing the simulated run length.
