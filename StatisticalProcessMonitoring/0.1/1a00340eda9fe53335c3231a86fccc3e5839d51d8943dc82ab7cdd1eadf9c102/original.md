```
run_sim(CH::AbstractChart, DGP::AbstractPhase2)
```

Simulates a run length for the control chart `CH` by sampling new data from the provided data-generating process `DGP`.

### Inputs

  * `CH` - A control chart.
  * `DGP` - An AbstractPhase2 object.

### Returns

  * An `Int` representing the simulated run length.
